---
title: L’installation d’Adobe Commerce 2.4.0 échoue avec un cache de magasins obsolète
description: 'Cet article fournit une solution au problème d’échec de votre installation d’Adobe Commerce 2.4.0 avec le message d’erreur suivant : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affiché dans la console.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%
---
# L’installation d’Adobe Commerce 2.4.0 échoue avec un cache de magasins obsolète

Cet article fournit une solution au problème d’échec de votre installation d’Adobe Commerce 2.4.0 avec le message d’erreur suivant : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* s’affiche dans la console.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Conditions préalables requises :</u>
Une extension tierce avec des dépendances sur les API pour le module Store dans les commandes CLI est configurée comme requis dans `composer.json`. Cela entraîne l’échec de l’installation d’Adobe Commerce 2.4.0 avec un message d’erreur : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* s’affiche dans la console.

## Cause

Le problème apparaît pour les extensions tierces qui possèdent des dépendances de magasins dans leurs commandes d’interface de ligne de commande. L’un d’eux est celui des canaux de vente Amazon.

## Solution

Avant l’installation d’Adobe Commerce 2.4.0, les commerçants doivent :

1. Supprimez ces extensions tierces de `composer.json`.
1. Installez Adobe Commerce sans extensions.
1. Ajoutez les extensions après l’installation.

Le problème sera corrigé dans le cadre de la version 2.4.1.

## Informations connexes dans notre base de connaissances de support :

* [Problème connu d’Adobe Commerce 2.4.0 : libellé « Remboursement » manquant dans Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0 et 2.4.1 : activer l’émission de facture partielle Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu dans Adobe Commerce 2.4.0 : Amazon Pay activé, modes de paiement manquants lorsque le retour à la caisse standard est utilisé](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

