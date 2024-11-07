---
title: '"Adobe Commerce 2.4.0 : "L’ajout de sélections à mon panier ne fonctionne pas"'
description: Cet article fournit une solution à un problème connu lié au bouton endommagé dans l’administrateur Commerce lors de la gestion du panier d’un client. Lorsque vous essayez d’ajouter des produits sélectionnés au panier d’un client, le bouton **Ajouter des sélections à mon panier** situé au bas de la section ne fonctionne pas. Ce problème se produit sur n’importe quelle page du panneau d’administration qui contient deux boutons **Ajouter des sélections à mon panier**. Un correctif permanent sera disponible dans Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas

Cet article fournit une solution à un problème connu lié au bouton endommagé dans l’administrateur Commerce lors de la gestion du panier d’un client. Lorsque vous essayez d’ajouter des produits sélectionnés au panier d’un client, le bouton **Ajouter des sélections à mon panier** situé au bas de la section ne fonctionne pas. Ce problème se produit sur n’importe quelle page du panneau d’administration qui contient deux boutons **Ajouter des sélections à mon panier** . Un correctif permanent sera disponible dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce 2.4.0 (toutes les méthodes de déploiement)

## Problème

<u>Étapes à reproduire</u>

1. Accédez à une page du panneau d’administration qui contient deux boutons **Ajouter des sélections à mon panier** .
1. Sélectionnez les éléments à ajouter à mon panier.
1. Cliquez sur le bouton **Ajouter des sélections à mon panier** situé au bas de la section.

<u>Résultat attendu</u>

Toutes les sélections sont ajoutées à mon panier comme prévu.

<u>Résultat réel</u>

Adobe Commerce n’ajoute pas vos sélections à mon panier.

## Solution

Le bouton **Ajouter des sélections à mon panier** situé en haut de la page fonctionne toujours. Le problème devrait être résolu dans la version 2.4.1 d&#39;Adobe Commerce, dont la sortie est prévue pour le quatrième trimestre.

## Lecture connexe

* [MerchDocs&#39; Gestion d’un panier](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) dans notre guide d’utilisation.
* [Problème connu d’Adobe Commerce 2.4.0 : les données de message brutes s’affichent sur storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) dans notre base de connaissances de support.
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) dans notre base de connaissances de prise en charge.
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse multi-adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) dans notre base de connaissances de support.
