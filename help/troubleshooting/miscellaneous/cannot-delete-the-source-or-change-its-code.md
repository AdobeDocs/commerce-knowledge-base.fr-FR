---
title: Impossible de supprimer la source ou de modifier son code
description: Cet article fournit un correctif pour les cas où vous ne pouvez pas supprimer complètement une source et/ou modifier son code.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Impossible de supprimer la source ou de modifier son code

Cet article fournit un correctif pour les cas où vous ne pouvez pas supprimer complètement une source et/ou modifier son code.

## Problème

Les sources ne peuvent pas être supprimées, quelle que soit l’attribution du produit.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes les versions), avec le stock de Magento installé
* Adobe Commerce On-Premise 2.3.0 et versions ultérieures, avec l’installation de Magento Inventory
* Magento Open Source 2.3.0 et versions ultérieures, avec l’inventaire du Magento installé

## Cause

Par conception, il n’est pas possible de supprimer complètement une source et/ou de modifier son code.

La suppression totale d’une source entraînerait des problèmes de données de commande, car les sources font partie des stocks de produits, des commandes, des données d’expédition, et bien plus encore.

Le code est essentiel pour connecter la source aux commandes. Il s’agit d’un identifiant unique de la source qui est désactivé lors de la modification.

## Solution

Vous pouvez supprimer une source d’un produit en transférant l’inventaire ou en déposant le produit de toutes les cargaisons à un emplacement donné.

Si vous devez supprimer une source de [SSA](https://devdocs.magento.com/guides/v2.3/inventory/source-selection-algorithms.html) calculs et traitement des commandes d’inventaire Adobe Commerce, vous pouvez désactiver la source. Les sources désactivées conservent toutes les données, les produits attribués et les quantités d’inventaire et peuvent être réactivées à tout moment pour recommencer l’expédition.

Voir [Guide de création de sources](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) pour plus d’informations sur la désactivation d’une source.
