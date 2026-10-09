---
title: 'problème connu d’Adobe Commerce 2.4.0 : Amazon pay, aucun mode de paiement'
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel des méthodes de paiement sont manquantes lorsque les clients utilisent **Retour à la commande standard** après avoir activé Amazon Pay.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# problème connu d’Adobe Commerce 2.4.0 : Amazon pay, aucun mode de paiement

Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel des méthodes de paiement sont manquantes lorsque les clients utilisent **Retour à la commande standard** après avoir activé Amazon Pay.

## Produits et versions concernés

Adobe Commerce on-premise et Adobe Commerce sur les infrastructures cloud v2.3.5.p1 et v2.4.0

<u>Procédure à suivre :</u>

1. Accédez au storefront.
1. Ajoutez n’importe quel article au panier et passez à la caisse.
1. Connectez-vous à votre compte Amazon Pay.
1. Sélectionnez une adresse et passez à la caisse.
1. Cliquez sur **Revenir à l’extraction standard**.
1. Passez à la caisse.

<u>Résultats attendus :</u>

Les modes de paiement doivent être affichés après le redémarrage du passage en caisse.

<u>Résultats réels:</u>

Les modes de paiement sont manquants.

## Solution

Une résolution est prévue pour la version 2.4.1.

## Informations connexes dans notre base de connaissances de support :

* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
