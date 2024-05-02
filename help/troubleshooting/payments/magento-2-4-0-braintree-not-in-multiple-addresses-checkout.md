---
title: "Adobe Commerce 2.4.0 : Braintree non pris en charge par plusieurs adresses"
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0, où les méthodes de paiement des Braintree ne sont pas incluses dans l’utilisation du passage en caisse de plusieurs adresses. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : passage en caisse pour les Braintree ne faisant pas partie de plusieurs adresses

Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0, où les méthodes de paiement des Braintree ne sont pas incluses dans l’utilisation du passage en caisse de plusieurs adresses. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.1.

Remarque : Adobe Commerce recommande d’utiliser la variable [Extension de Braintree de Commerce Marketplace](https://marketplace.magento.com/paypal-module-braintree.html) pour les versions 2.3 et ultérieures afin de respecter le PSD. L’extension ne propose pas la fonctionnalité de passage en caisse à plusieurs adresses.

## Produits et versions concernés

* Adobe Commerce sur site v2.4.0
* Adobe Commerce sur l’infrastructure cloud v2.4.0

## Problème

<u>Conditions préalables</u>:

L’intégration de Braintree principal est utilisée.

<u>Étapes à reproduire</u>:

1. Allez à la vitrine.
1. Connectez-vous en tant que client.
1. Ajoutez un produit au panier.
1. Ouvrez votre panier.
1. Presse **Afficher et modifier le panier**.
1. Presse **Extraction avec plusieurs adresses**.
1. Presse **Accéder aux informations d’expédition**.
1. Presse **Continuer vers les informations de facturation**.

<u>Résultat attendu</u>:

Braintree est disponible en tant que mode de paiement.

<u>Résultat réel</u>:

Braintree n’est pas disponible en tant que mode de paiement.

## Solution

N’activez pas les options à plusieurs adresses si vous utilisez Braintree dans Adobe Commerce 2.4.0. Ce problème a été corrigé dans Adobe Commerce 2.4.1.

## Lecture connexe dans notre base de connaissances de soutien

* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
