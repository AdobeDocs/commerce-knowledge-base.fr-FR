---
title: 'Adobe Commerce 2.4.0 : passage en caisse de Braintree absent de plusieurs adresses'
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel les méthodes de paiement Braintree ne sont pas incluses dans le passage en caisse avec plusieurs adresses. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '232'
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
