---
title: L’installation d’Adobe Commerce 2.4.0 échoue avec un cache de magasins obsolète
description: 'Cet article fournit une solution au problème d’échec de votre installation d’Adobe Commerce 2.4.0 avec le message d’erreur suivant : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affiché dans la console.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# L’installation d’Adobe Commerce 2.4.0 échoue avec un cache de magasins obsolète

Cet article fournit une solution au problème d’échec de votre installation d’Adobe Commerce 2.4.0 avec le message d’erreur suivant : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affichées dans la console.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Conditions préalables : </u>
Une extension tierce avec des dépendances sur les API pour le module Store dans les commandes CLI est configurée comme requis dans `composer.json`. Cela entraîne l’échec de l’installation d’Adobe Commerce 2.4.0 avec un message d’erreur : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affichées dans la console.

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
* [L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

