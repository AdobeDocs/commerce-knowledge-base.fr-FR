---
title: La base de données contient plusieurs lignes pour la même entité
description: Cet article fournit une solution au problème où il existe plusieurs lignes pour le même ID d’entité dans la base de données.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
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

Où `$entityID = ID` de la page CMS/règle de prix de catégorie/produit/panier/règle de prix de catalogue/règle de prix de catalogue

| Entité | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Catégorie/produit | catalog_category_entity/catalog_product_entity | entity_id |
| Règle de prix du panier/Règle de prix du catalogue | salesrule/catalogrule | rule_id |
| Page CMS | cms_page | page_id |

## Cause

Il s’agit du comportement attendu. Les différentes lignes sont créées par la fonctionnalité d’évaluation de contenu :

* Si vous spécifiez une date de début sans date de fin, il y aura au moins deux lignes avec le même ID d’entité/de règle/de page. Une ligne indique l’état d’origine de l’entité (la ligne dans laquelle `created_in=1`) et une autre indique la *fin de la mise à jour planifiée*.

* Si vous spécifiez une date de début avec une date de fin, il y aura au moins trois lignes avec le même ID d’entité/de règle/de page. Une ligne indique l’état d’origine de l’entité (la ligne dans laquelle `created_in=1`), une ligne correspond au *Début de la mise à jour planifiée* et une ligne correspond à la *Fin de la mise à jour planifiée*.

Par exemple, dans cette requête :

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* Les valeurs `created_in` et `updated_in` doivent suivre ce modèle : la valeur `created_in` de la ligne actuelle est égale à la valeur `updated_in` de la ligne précédente. En outre, la première ligne doit contenir `created_in = 1` et la dernière ligne doit contenir `updated_in = 2147483647`. (S’il n’y a qu’une seule ligne, vous devez voir `created_in=1` et `updated_in=2147483647`).

### Pourquoi la deuxième entrée DB (et toutes les entrées suivantes) apparaît-elle dans DB pour la même entité ?

* Le deuxième enregistrement DB (et, éventuellement, les suivants) pour l’entité affectée signifie qu’il y a eu des mises à jour d’évaluation de contenu planifiées à l’aide du module `Magento_Staging`, ce qui crée un enregistrement supplémentaire pour une entité dans les tables respectives.

Un problème se produirait uniquement si les enregistrements ont les mêmes valeurs pour les colonnes `created_in` ou `updated_in`.

## Solution

Il s’agit du comportement attendu qui ne provoquera des problèmes que s’il existe des incohérences entre les lignes.

## Lecture connexe

* [Les modifications apportées aux catégories ne sont pas enregistrées](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html?lang=fr) dans notre base de connaissances de l’assistance
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
