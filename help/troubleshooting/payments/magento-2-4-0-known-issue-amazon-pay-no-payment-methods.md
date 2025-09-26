---
title: 'problème connu d’Adobe Commerce 2.4.0 : Amazon pay, aucun mode de paiement'
description: Cet article fournit une solution à un problème connu d’Adobe Commerce 2.4.0 en raison duquel des méthodes de paiement sont manquantes lorsque les clients utilisent **Retour à la commande standard** après avoir activé Amazon Pay.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 60f68b9edabd13a69e84705b85d84fd10ee6e2be
workflow-type: tm+mt
source-wordcount: '258'
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
* [L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe à l’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton « Ajouter des sélections à mon panier » ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
