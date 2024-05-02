---
title: "Adobe Commerce 2.3.6 : compteur sans fin affiché lors de l’enregistrement de l’adresse"
description: Cet article décrit un problème connu d’Adobe Commerce 2.3.6, où le compteur d’attente s’affiche indéfiniment lors de l’enregistrement d’une adresse dans Mon compte sur le storefront.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6 : compteur sans fin affiché lors de l’enregistrement de l’adresse

Cet article décrit un problème connu d’Adobe Commerce 2.3.6, où le compteur d’attente s’affiche indéfiniment lors de l’enregistrement d’une adresse dans Mon compte sur le storefront.

## Produits et versions concernés

* Adobe Commerce 2.3.6 avec l’intégration de Vertex activée (navigateur Firefox uniquement)

## Problème

Lors de l’enregistrement d’une adresse dans la section Mon compte sur le storefront, le compteur d’attente s’affiche parfois indéfiniment en raison d’une erreur dans le fichier JS principal Vertex.

## Solution

Solution : utilisez un autre navigateur que Firefox.

Le problème a été corrigé dans Adobe Commerce 2.3.1.

## Lecture connexe

* [Différentes adresses non autorisées lors de la désélection de l’option &quot;Mes adresses de facturation et de livraison sont identiques&quot; à l’aide du nettoyage des adresses de sommet](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) dans notre base de connaissances de soutien.
* [Mise à jour de l’adresse de message après validation de l’adresse du sommet Adobe Commerce 2.4.1](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) dans notre base de connaissances de soutien.
