---
title: Dépannage de l’outil de migration de données
description: Cet article fournit des solutions aux erreurs qui peuvent se produire lors de l’exécution de l’outil de migration des données.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Dépannage de l’outil de migration de données

Cet article fournit des solutions aux erreurs qui peuvent se produire lors de l’exécution de l’outil de migration des données.

## Documents/champs source non mappés {#source-documents-fields-not-mapped}

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

plutôt que les sources.

### Cause

Certaines entités d’Adobe Commerce version 1 (provenant dans la plupart des cas d’extensions) n’existent pas dans la base de données d’Adobe Commerce version 2.

Ce message s’affiche, car l’outil de migration de données exécute des tests internes pour vérifier que les tableaux et les champs sont cohérents entre *source* (Adobe Commerce 1) et *destination* (Adobe Commerce 2) bases de données.

### Solutions possibles

* Installez les extensions Adobe Commerce 2 correspondantes depuis [Commerce Marketplace](https://marketplace.magento.com/).     Si les données en conflit proviennent d’une extension qui ajoute ses propres éléments de structure de base de données, la version Adobe Commerce 2 de la même extension peut ajouter de tels éléments à la base de données de destination (Adobe Commerce 2), ce qui corrige le problème.
* Utilisez la variable `-a` lors de l’exécution de l’outil pour résoudre automatiquement les erreurs et empêcher l’arrêt de la migration.
* Configurez l’outil pour ignorer les données problématiques.

Pour ignorer les entités de base de données, ajoutez le `<ignore>` vers une entité dans la balise `map.xml` comme ceci :

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
>Avant d’ignorer les entités par fichier de mappage ou à l’aide de la variable `-a` , assurez-vous que vous n’avez pas besoin des données concernées dans votre boutique Adobe Commerce 2.

## Classe non mappée dans l’enregistrement {#class-does-not-exist-but-mentioned}

### Message d’erreur

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Cause

Une classe du code base Adobe Commerce 1 est introuvable dans le code base Adobe Commerce 2 pendant la [Etape de migration EAV](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) dans notre documentation destinée aux développeurs. Dans la plupart des cas, la classe manquante appartient à une [extension](https://glossary.magento.com/extension).

### Solutions possibles

* Installez l’extension Adobe Commerce 2 correspondante.
* Ignorez l’attribut qui génère le problème.    Pour ce faire, ajoutez l’attribut à la variable `ignore` du groupe `eav-attribute-groups.xml.dist` fichier .
* Ajoutez un mappage de classe à l’aide de la fonction `class-map.xml.dist` fichier .

## Échec de la contrainte de clé étrangère

### Texte du message d’erreur

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Cause

Il manque des enregistrements de base de données dans la variable `parent_table` auquel la variable `field_id` de `child_table` pointe vers .

### Solution possible

Supprimez les enregistrements du `child_table` , si vous n’en avez pas besoin.

Pour conserver les enregistrements, désactivez la variable `Data Integrity Step` en modifiant les `config.xml` .

## Doublons dans les réécritures d’URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Cause

La variable `Target path` dans une réécriture d’URL doit être spécifiée par une paire unique de `Request path` + `Store ID` . Cette erreur signale deux entrées qui utilisent la même `Request path` + `Store ID` paire avec deux différents `Target path` valeurs.

### Solution possible

Activez la variable `auto_resolve_urlrewrite_duplicates` dans votre `config.xml` fichier .

Cette configuration ajoute une chaîne de hachage aux enregistrements en conflit de [URL](https://glossary.magento.com/url) réécrit et affiche le résultat de la résolution dans votre interface de ligne de commande.

## Discordance des entités {#mismatch-of-entities}

### Message d’erreur

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Cause

L’erreur se produit lors de l’étape Vérification du volume . Cela signifie que le nombre d’enregistrements de la base de données Adobe Commerce 2 du document n’est pas le même que dans Adobe Commerce 1.

Des enregistrements manquants se produisent lorsqu’un client passe une commande lors de la migration.

### Solution possible

Exécution de l’outil de migration des données dans `Delta` pour transférer les modifications incrémentielles.

## Deltalog n’est pas installé {#deltalog-is-not-installed}

### Message d’erreur

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Cause

Cette erreur se produit pendant [migration incrémentale](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (dans la documentation destinée aux développeurs) des modifications apportées aux données. Cela signifie décharger les tables (avec préfixe) `m2_cl_*`) sont introuvables dans la base de données Adobe Commerce 1. L’outil installe ces tables pendant la [migration des données](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (dans notre documentation destinée aux développeurs) ainsi que les déclencheurs de base de données qui effectuent le suivi des modifications et remplissent les tables de décompression.

L’erreur peut être due au fait que vous essayez de migrer à partir d’un *copy* de votre boutique Adobe Commerce 1 active, et non du magasin en ligne lui-même. Lorsque vous effectuez une copie à partir d’un magasin Adobe Commerce 1 actif qui n’a jamais été migré, la copie ne contient pas les déclencheurs et les tables de suppression supplémentaires nécessaires pour terminer une migration delta, de sorte que la migration échoue. L’outil de migration de données ne fait PAS de comparaisons entre la base de données d’AC1 et d’AC2 pour migrer les différences. Au lieu de cela, l’outil utilise les déclencheurs et les tables de suppression installés lors de la première migration pour effectuer les migrations delta suivantes. Dans ce cas, votre copie de la base de données Adobe Commerce 1 active ne contient pas les déclencheurs et les tables de déverrouillage utilisés par l’outil de migration des données pour effectuer une migration.

### Solution possible

Nous vous recommandons de tester le processus de migration à partir d’une copie de votre base de données Adobe Commerce 1 afin de résoudre vos problèmes de migration. Après avoir corrigé les problèmes de la copie, relancez le processus de migration à partir de votre base de données Adobe Commerce 1 active. Cela permettra d’assurer un processus de migration fluide.
