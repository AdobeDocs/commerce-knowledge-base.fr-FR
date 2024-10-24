---
title: "Problème connu d’Adobe Commerce 2.4.0 : paiement Amazon, aucun mode de paiement"
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel les méthodes de paiement sont manquantes lorsque les clients utilisent **Revenir à la caisse standard**, après avoir activé le paiement Amazon.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 : paiement Amazon, aucun mode de paiement

Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 qui fait défaut lorsque des méthodes de paiement sont manquantes lorsque les clients utilisent **Revenir au passage en caisse standard**, après avoir activé le paiement Amazon.

## Produits et versions concernés

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud v2.3.5.p1 et v2.4.0

<u>Étapes à reproduire :</u>

1. Accédez au storefront.
1. Ajoutez n’importe quel élément au panier et passez au passage en caisse.
1. Connectez-vous à votre compte de paiement Amazon.
1. Sélectionnez une adresse et passez à la caisse.
1. Cliquez sur **Revenir au passage en caisse standard**.
1. Passez à la caisse.

<u>Résultats attendus :</u>

Les modes de paiement doivent s’afficher après le redémarrage du paiement.

<u>Résultats réels :</u>

Les modes de paiement sont manquants.

## Solution

Une résolution est prévue pour la version 2.4.1.

## Lectures connexes dans notre base de connaissances de support :

* [Problème connu d’Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur 404 lors de la suppression des points de récompense lors du passage en caisse multi-expédition](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
