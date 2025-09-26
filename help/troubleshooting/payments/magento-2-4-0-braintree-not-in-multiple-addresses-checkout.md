---
title: 'Adobe Commerce 2.4.0 : passage en caisse de Braintree absent de plusieurs adresses'
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel les méthodes de paiement Braintree ne sont pas incluses dans le passage en caisse avec plusieurs adresses. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : passage en caisse de Braintree absent de plusieurs adresses

Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel les méthodes de paiement Braintree ne sont pas incluses dans le passage en caisse avec plusieurs adresses. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.

Remarque : Adobe Commerce recommande d’utiliser l’extension Braintree [Commerce Marketplace](https://marketplace.magento.com/paypal-module-braintree.html) pour les versions 2.3 et ultérieures afin de maintenir la conformité PSD. L’extension n’offre pas la fonctionnalité de passage en caisse à adresses multiples.

## Produits et versions concernés

* Adobe Commerce on-premise v2.4.0
* Adobe Commerce sur les infrastructures cloud v2.4.0

## Problème

<u>Conditions préalables</u> :

L’intégration Braintree de base est utilisée.

<u>Procédure à suivre </u> :

1. Allez à la vitrine.
1. Connectez-vous en tant que client.
1. Ajoutez un produit au panier.
1. Ouvrez votre panier.
1. Appuyez sur **Afficher et modifier le panier**.
1. Appuyez sur **Extraire avec plusieurs adresses**.
1. Appuyez sur **Accéder aux informations d’expédition**.
1. Appuyez sur **Continuer vers les informations de facturation**.

<u>Résultat attendu </u> :

Braintree est disponible en tant que mode de paiement.

<u>Résultat réel</u> :

Braintree n&#39;est pas disponible comme mode de paiement.

## Solution

N’activez pas les options à adresses multiples si vous utilisez Braintree dans Adobe Commerce 2.4.0. Ce problème a été résolu dans Adobe Commerce 2.4.1.

## Lectures connexes dans notre base de connaissances de support

* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe à l’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton « Ajouter des sélections à mon panier » ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
