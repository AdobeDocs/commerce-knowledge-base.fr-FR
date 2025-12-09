---
title: 'Adobe Commerce 2.3.6 : une double flèche sans fin affichée lors de l’enregistrement de l’adresse'
description: Cet article décrit un problème Adobe Commerce 2.3.6 connu, où la double flèche en attente s’affiche indéfiniment lors de l’enregistrement d’une adresse dans Mon compte sur le storefront.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Adobe Commerce 2.3.6 : une double flèche sans fin affichée lors de l’enregistrement de l’adresse

Cet article décrit un problème Adobe Commerce 2.3.6 connu, où la double flèche en attente s’affiche indéfiniment lors de l’enregistrement d’une adresse dans Mon compte sur le storefront.

## Produits et versions concernés

* Adobe Commerce 2.3.6 avec intégration de Vertex activée (navigateur Firefox uniquement)

## Problème

Lors de l’enregistrement d’une adresse dans la section Mon compte du storefront, la double flèche en attente s’affiche parfois indéfiniment en raison d’une erreur dans Vertex core JS.

## Solution

Solution : utilisez un autre navigateur que Firefox.

Le problème a été résolu dans Adobe Commerce 2.3.1.

## Lecture connexe

* [Message de validation d’adresse de sommet Adobe Commerce 2.4.1 après la mise à jour de l’adresse](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) dans notre base de connaissances d’assistance.
