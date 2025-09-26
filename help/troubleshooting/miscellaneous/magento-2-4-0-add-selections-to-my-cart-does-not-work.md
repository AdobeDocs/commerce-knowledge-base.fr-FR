---
title: 'Adobe Commerce 2.4.0 : « Ajouter des sélections à mon panier » ne fonctionne pas'
description: Cet article fournit une solution à un problème connu du bouton rompu dans l’administration Commerce lors de la gestion du panier d’un client. Lorsque vous essayez d’ajouter des produits sélectionnés au panier d’un client ou d’une cliente, le bouton **Ajouter des sélections à mon panier** situé au bas de la section ne fonctionne pas. Ce problème se produit sur n’importe quelle page du panneau d’administration contenant deux boutons **Ajouter des sélections à mon panier**. Un correctif permanent sera disponible dans Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : « Ajouter des sélections à mon panier » ne fonctionne pas

Cet article fournit une solution à un problème connu du bouton rompu dans l’administration Commerce lors de la gestion du panier d’un client. Lorsque vous essayez d’ajouter des produits sélectionnés au panier d’un client ou d’une cliente, le bouton **Ajouter des sélections à mon panier** situé au bas de la section ne fonctionne pas. Ce problème se produit sur n’importe quelle page du panneau d’administration contenant deux boutons **Ajouter des sélections à mon panier**. Un correctif permanent sera disponible dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce 2.4.0 (toutes les méthodes de déploiement)

## Problème

<u>Procédure à suivre</u>

1. Accédez à n’importe quelle page du panneau d’administration contenant deux boutons **Ajouter des sélections à mon panier**.
1. Sélectionner les articles à ajouter à mon panier.
1. Cliquez sur le bouton **Ajouter des sélections à mon panier** situé au bas de la section.

<u>Résultat attendu</u>

Toutes les sélections sont ajoutées à mon panier comme prévu.

<u>Résultat réel</u>

Adobe Commerce n’ajoute pas vos sélections à mon panier.

## Solution

Le bouton **Ajouter des sélections à mon panier** situé en haut de la page fonctionne toujours. Le problème devrait être corrigé dans la version 2.4.1 d’Adobe Commerce, dont la publication est prévue pour le 4e trimestre.

## Lecture connexe

* [MerchDocs’ Gérer un panier](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) dans notre guide de l’utilisateur.
* [Problème connu d&#39;Adobe Commerce 2.4.0 : les taux de taxe à l&#39;exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) dans notre base de connaissances de support.
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) dans notre base de connaissances d’assistance.
