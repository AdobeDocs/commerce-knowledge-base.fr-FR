---
title: Problème connu du comptage de produit d’action en bloc dans Adobe Commerce 2.3.5
description: Cet article décrit un problème connu d’Adobe Commerce 2.3.5, où la notification qu’un commerçant reçoit après une action en masse dans Admin contient un nombre incorrect d’articles affectés.
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Problème connu du comptage de produit d’action en bloc dans Adobe Commerce 2.3.5

Cet article décrit un problème connu d’Adobe Commerce 2.3.5, où la notification qu’un commerçant reçoit après une action en masse dans Admin contient un nombre incorrect d’articles affectés.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.5
* Adobe Commerce on-premise 2.3.5

## Problème

Le message système affiché par Adobe Commerce après une action en bloc (par exemple, une mise à jour de produit en masse ou un import/export) affiche 0 au lieu d’un comptage précis des produits affectés par l’action en masse.

## Correction

Un correctif sera disponible dans Adobe Commerce 2.3.6, dont la sortie est prévue au quatrième trimestre 2020.

## Lecture connexe

* Articles de la base de connaissances de la prise en charge d’Adobe Commerce pour les problèmes connus d’Adobe Commerce 2.3.5 :
   * [Commandes multi-expédition avec un produit virtuel non traité correctement dans Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Problème connu de la comparaison de produits dans Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Correctif du problème de paiement Amazon dans Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [Adobe Commerce 2.3.5 Problèmes connus dans notre documentation destinée aux développeurs](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
