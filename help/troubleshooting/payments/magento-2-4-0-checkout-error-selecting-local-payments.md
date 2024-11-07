---
title: "Adobe Commerce 2.4.0 : erreur de paiement lors de la sélection des paiements locaux"
description: "Cet article parle d’une solution à un problème connu dans Adobe Commerce lors du passage en caisse, où un message d’erreur s’affiche lors de la sélection d’un mode de paiement local pour certains pays. Cela se produit pour les pays suivants : Belgique, Italie, Pays-Bas, Pologne et Espagne."
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : erreur de paiement lors de la sélection des paiements locaux

Cet article traite d’une solution à un problème connu dans Adobe Commerce lors du passage en caisse, où un message d’erreur s’affiche lors de la sélection d’un mode de paiement local pour certains pays. Cela se produit pour les pays suivants : Belgique, Italie, Pays-Bas, Pologne et Espagne.

Message d’erreur, &quot;*&quot; Il n’existe actuellement aucun mode de paiement disponible. Mettez à jour votre adresse de facturation.*&quot; s’affiche, mais les méthodes de paiement locales continuent d’apparaître et de fonctionner correctement. Un correctif permanent sera disponible dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables</u> :

* Adobe Commerce 2.4.0 est installé.
* Créez un produit et une catégorie.
* Configurez le [mode de paiement du Braintree](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree.html).

<u>Étapes à reproduire</u> :

1. Accédez au storefront.
1. Sélectionnez les éléments à ajouter au panier.
1. Passez à la caisse.
1. Remplissez le formulaire d’adresse avec une adresse valide.
1. Accédez à la page Révision et paiements .

<u>Résultat attendu</u> :

Les modes de paiement locaux doivent s&#39;afficher normalement, sans message d&#39;erreur.

<u>Résultat réel</u> :

Message d’erreur, &quot;*&quot; Il n’existe actuellement aucun mode de paiement disponible. Mettez à jour votre adresse de facturation.*&quot; s’affiche, mais les méthodes de paiement locales s’affichent toujours et fonctionnent correctement.

## Solution

La solution consiste à ignorer le message d’erreur affiché et à poursuivre le paiement normalement, car tous les modes de paiement locaux fonctionneront normalement. Le correctif était disponible à partir de la version 2.4.1 d’Adobe Commerce.

## Lecture connexe

* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : retourne l’arrêt de la page d’édition lors de la création du libellé d’expédition](/help/troubleshooting/known-issues-patches-attached/magento-2-4-0-patch-returns-shipping-label-creation-issue.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
