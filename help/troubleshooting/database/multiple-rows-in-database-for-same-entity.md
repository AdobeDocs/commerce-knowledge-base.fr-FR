---
title: La base de données contient plusieurs lignes pour la même entité
description: Cet article fournit une solution au problème où il existe plusieurs lignes pour le même ID d’entité dans la base de données.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Plusieurs lignes dans la base de données pour la même entité

Cet article fournit une solution au problème où il existe plusieurs lignes pour le même ID d’entité dans la base de données.

## Produits et versions concernés :

* Adobe Commerce (toutes versions)

## Problème

Il existe plusieurs lignes pour le même ID d’entité dans la base de données.

Par exemple, après avoir reçu une liste d’enregistrements avec des identifiants d’entité en double lors de l’exécution de cette requête :

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Où `$entityID = ID` de la page CMS/règle de prix de catégorie/produit/panier/règle de prix de catalogue/page CMS.

| Entité | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Catégorie/produit | catalog_category_entity/catalog_product_entity | entity_id |
| Règle de prix du panier/Règle de prix du catalogue | salesrule/catalogrule | rule_id |
| Page CMS | cms_page | page_id |

## Cause

Il s’agit du comportement attendu. Les différentes lignes sont créées par la fonctionnalité d’évaluation de contenu :

* Si vous spécifiez une date de début sans date de fin, il y aura au moins deux lignes avec le même ID d’entité/de règle/de page. Une ligne indique l’état d’origine de l’entité (la ligne dans laquelle `created_in=1`), et une ligne indique le *Fin de la mise à jour planifiée*.

* Si vous spécifiez une date de début avec une date de fin, il y aura au moins trois lignes avec le même ID d’entité/de règle/de page. Une ligne indique l’état d’origine de l’entité (la ligne dans laquelle `created_in=1`), une ligne correspond au *Début de la mise à jour planifiée*, et une ligne correspond au *Fin de la mise à jour planifiée*.

Par exemple, dans cette requête :

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* La variable `created_in` et `updated_in` Les valeurs doivent suivre ce modèle : `created_in` La valeur de la ligne actuelle est égale à la valeur de la ligne `updated_in` dans la ligne précédente. La première ligne doit également contenir `created_in = 1` et la dernière ligne doit contenir `updated_in = 2147483647`. (S’il n’y a qu’une seule ligne, vous devez voir `created_in=1` et `updated_in=2147483647`).

### Pourquoi la deuxième entrée DB (et toutes les entrées suivantes) apparaît-elle dans DB pour la même entité ?

* Le deuxième enregistrement DB (et, éventuellement, les suivants) pour l’entité affectée signifie qu’il y a eu des mises à jour d’évaluation de contenu planifiées à l’aide de la variable `Magento_Staging` qui crée un enregistrement supplémentaire pour une entité dans les tables respectives.

Un problème se produirait uniquement si les enregistrements ont les mêmes valeurs pour la variable `created_in` ou `updated_in` colonnes.

## Solution

Il s’agit du comportement attendu qui ne provoquera des problèmes que s’il existe des incohérences entre les lignes.

## Lecture connexe

* [Les modifications apportées aux catégories ne sont pas enregistrées.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html) dans notre base de connaissances de soutien.
* [Dupliquer les entrées dans la table du catalogue après avoir modifié la date de fin d’une mise à jour de planning](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) dans notre base de connaissances de soutien.
