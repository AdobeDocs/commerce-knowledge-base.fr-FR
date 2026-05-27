---
title: Dépannage de l’outil de migration de données
description: Cet article fournit des solutions pour les erreurs qui peuvent se produire lorsque vous exécutez l’outil de migration des données.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# Dépannage de l’outil de migration de données

Cet article fournit des solutions pour les erreurs qui peuvent se produire lorsque vous exécutez l’outil de migration des données.

## Documents/champs Source non mappés {#source-documents-fields-not-mapped}

### Messages d’erreur

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

Dans de rares cas, le message peut mentionner

```bash
Destination documents
```

ou

```bash
Destination fields
```

au lieu des sources.

### Cause

Certaines entités Adobe Commerce version 1 (provenant le plus souvent d’extensions) n’existent pas dans la base de données Adobe Commerce version 2.

Ce message s’affiche, car l’outil de migration des données exécute des tests internes pour vérifier que les tables et les champs sont cohérents entre les bases de données *source* (Adobe Commerce 1) et *destination* (Adobe Commerce 2).

### Solutions possibles

* Installez les extensions Adobe Commerce 2 correspondantes depuis [Commerce Marketplace](https://marketplace.magento.com/).     Si les données en conflit proviennent d’une extension qui ajoute ses propres éléments de structure de base de données, la version Adobe Commerce 2 de la même extension peut ajouter ces éléments à la base de données de destination (Adobe Commerce 2), ce qui résout le problème.
* Utilisez l’argument `-a` lors de l’exécution de l’outil pour résoudre automatiquement les erreurs et empêcher l’arrêt de la migration.
* Configurez l’outil pour ignorer les données problématiques.

Pour ignorer les entités de la base de données, ajoutez la balise `<ignore>` à une entité dans le fichier `map.xml`, comme suit :

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Avant d’ignorer des entités par mappage de fichier ou d’utiliser l’option `-a` , assurez-vous de ne pas avoir besoin des données concernées dans votre boutique Adobe Commerce 2.

## La classe n’est pas mappée dans l’enregistrement {#class-does-not-exist-but-mentioned}

### Message d’erreur

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Cause

Une classe de la base de code Adobe Commerce 1 est introuvable dans la base de code Adobe Commerce 2 lors de l’étape [migration EAV](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/basics/technical-specification) dans notre documentation destinée aux développeurs. Dans la plupart des cas, la classe manquante appartient à une [ extension ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/glossary#extension).

### Solutions possibles

* Installez l’extension Adobe Commerce 2 correspondante.
* Ignorez l’attribut qui cause le problème.    Pour ce faire, ajoutez l’attribut au groupe de `ignore` dans le fichier `eav-attribute-groups.xml.dist` .
* Ajoutez un mappage de classe à l’aide du fichier `class-map.xml.dist`.

## Échec de la contrainte de clé étrangère

### Texte du message d’erreur

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Cause

Il manque des enregistrements de base de données dans le `parent_table` vers lequel pointe le `field_id` du `child_table`.

### Solution possible

Supprimez les enregistrements du `child_table` , si vous n’en avez pas besoin.

Pour conserver les enregistrements, désactivez la `Data Integrity Step` en modifiant la `config.xml` de l’outil de migration de données.

## Doublons dans les réécritures d’URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Cause

La `Target path` d’une réécriture d’URL doit être spécifiée par une paire unique `Request path` + `Store ID` . Cette erreur signale deux entrées qui utilisent la même paire `Request path` + `Store ID` avec deux valeurs de `Target path` différentes.

### Solution possible

Activez l’option `auto_resolve_urlrewrite_duplicates` dans votre fichier `config.xml`.

Cette configuration ajoute une chaîne de hachage aux enregistrements en conflit des réécritures d’URL et affiche le résultat de la résolution dans votre interface de ligne de commande.

## Discordance des entités {#mismatch-of-entities}

### Message d’erreur

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Cause

L’erreur se produit lors de l’étape de vérification du volume. Cela signifie que le nombre d’enregistrements de la base de données Adobe Commerce 2 du document n’est pas le même que dans Adobe Commerce 1.

Des enregistrements manquants se produisent lorsqu’un client passe une commande pendant la migration.

### Solution possible

Exécutez l’outil de migration de données en mode `Delta` pour transférer les modifications incrémentielles.

## Deltalog n&#39;est pas installé {#deltalog-is-not-installed}

### Message d’erreur

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Cause

Cette erreur se produit lors de la [migration incrémentielle](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/migrate-data/delta) (dans notre documentation destinée aux développeurs) des modifications apportées aux données. Cela signifie que les tables deltalog (avec le préfixe `m2_cl_*`) sont introuvables dans la base de données Adobe Commerce 1. Cet outil installe ces tables lors de la [migration des données](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/migrate-data/data) (dans notre documentation destinée aux développeurs) ainsi que des déclencheurs de base de données qui effectuent le suivi des modifications et renseignent les tables du deltalog.

L’une des raisons de l’erreur peut être que vous tentez d’effectuer une migration à partir d’une *copie* de votre boutique Adobe Commerce 1 active, et non à partir de la boutique en ligne elle-même. Lorsque vous effectuez une copie à partir d’un magasin Adobe Commerce 1 actif qui n’a jamais été migré, la copie ne contient pas les déclencheurs et les tables deltalog supplémentaires nécessaires pour terminer une migration delta. La migration échoue donc. L’outil de migration des données n’effectue PAS de comparaisons entre la base de données d’AC1 et d’AC2 pour migrer les différences. Au lieu de cela, l’outil utilise les déclencheurs et les tables de delta installées lors de la première migration afin d’effectuer les migrations delta suivantes. Dans ce cas, votre copie de la base de données Adobe Commerce 1 active ne contiendra pas les déclencheurs et les tables de deltalog que l’outil de migration de données utilise pour effectuer une migration.

### Solution possible

Nous vous avons recommandé de tester le processus de migration à partir d’une copie de votre base de données Adobe Commerce 1 pour résoudre vos problèmes de migration. Après avoir résolu les problèmes sur la copie, relancez le processus de migration à partir de votre base de données Adobe Commerce 1 active. Cela permettra d’assurer un processus de migration fluide.

## Lecture connexe

[Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

