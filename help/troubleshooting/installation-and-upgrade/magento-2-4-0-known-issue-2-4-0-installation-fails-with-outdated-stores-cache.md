---
title: Échec de l’installation d’Adobe Commerce 2.4.0 avec le cache de magasins obsolète
description: "Cet article fournit une solution au problème d’échec de l’installation d’Adobe Commerce 2.4.0 avec le message d’erreur : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affiché dans la console."
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Échec de l’installation d’Adobe Commerce 2.4.0 avec le cache de magasins obsolète

Cet article fournit une solution au problème d’échec de l’installation d’Adobe Commerce 2.4.0 avec le message d’erreur : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affiché dans la console.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Conditions préalables :</u>
Une extension tierce avec des dépendances sur les API pour le module Store dans les commandes de l’interface de ligne de commande est configurée comme requis dans `composer.json`. Cela entraîne l’échec de l’installation d’Adobe Commerce 2.4.0 avec un message d’erreur : *Le site web par défaut n’est pas défini. Définissez le site web et réessayez.* affiché dans la console.

## Cause

Le problème s’affiche pour les extensions tierces qui dépendent des magasins dans leurs commandes d’interface de ligne de commande. L’un est les Sales Channel Amazon.

## Solution

Avant l&#39;installation d&#39;Adobe Commerce 2.4.0, les commerçants doivent :

1. Supprimer ces extensions tierces de `composer.json`.
1. Installez Adobe Commerce sans extensions.
1. Ajoutez les extensions après l’installation.

Le problème sera corrigé dans la portée de la version 2.4.1.

## Lectures connexes dans notre base de connaissances de support :

* [Problème connu d&#39;Adobe Commerce 2.4.0 : absence de l&#39;étiquette &quot;Remboursement&quot; en larna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problème connu d’Adobe Commerce 2.4.0 : absence de deux boutons sur la page Créer une commande dans Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1 : activation du problème de facture partielle Venmo Braintree](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problème connu d’Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu d’Adobe Commerce 2.4.0 : paiement Amazon activé, méthodes de paiement manquantes lors du retour au paiement standard utilisé](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur 404 lors de la suppression des points de récompense lors du passage en caisse multi-expédition](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
