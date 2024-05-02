---
title: '''Problème connu d''Adobe Commerce 2.4.0 : absence de l''étiquette "Remboursement" en klarna'''
description: Cet article fournit une solution à un problème connu dans Admin pour une étiquette **Refund** manquante dans Klarna VBE (fournisseur Bundled Extension). Lorsque sur le portail de Klarna un remboursement est effectué, l'étiquette **Remboursement** n'est pas affichée en regard du Produit groupé qui a été remboursé.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Problème connu d&#39;Adobe Commerce 2.4.0 : absence de l&#39;étiquette &quot;Remboursement&quot; en larna

Cet article fournit une solution à un problème connu dans Admin pour un problème manquant **Remboursement** libellé dans Klarna VBE (Fournisseur groupé Extension). Lorsqu&#39;un remboursement est effectué sur le portail de Klarna, la variable **Remboursement** Le libellé n&#39;est pas affiché en regard du Produit groupé qui a été remboursé.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables :</u>

* La larna est activée.
* Un produit groupé est créé.

<u>Étapes à reproduire</u>

1. Accédez à Adobe Commerce front-end et ajoutez un produit groupé à **panier**.
1. Accédez à passage en caisse.
1. Saisie des informations sur le consommateur dans le passage en caisse et clic **Suivant**.
1. Sélectionner **Option KP** et cliquez sur **Passer commande**.
1. Accédez à **Administration** > **Ventes** > **Commandes**.
1. Ouvrez la commande.
1. Créer une facture pour le produit.
1. Accédez à **Facturations** > **Sélectionner une facture** > Cliquez sur **Crédit** > Cliquez sur **Remboursement** (Sauf **Remboursement hors ligne**).
1. Accédez au portail Klarna.
1. Ouvrez la commande.
1. La variable **Remboursement** est présent.

<u>Résultat attendu</u>

Sur le portail Klarna, la **Remboursement** le libellé est affiché en regard du produit qui a été remboursé.

<u>Résultat réel</u>

Sur le portail Klarna, la **Remboursement** le libellé n’est pas affiché en regard du produit qui a été remboursé.

## Solution

La solution à ce problème consiste à ignorer l’élément manquant **Remboursement** sur le portail Klarna pour les produits en vrac remboursés. Le remboursement a eu lieu, même si la variable **Remboursement** ne s’affichait pas. Le problème devrait être résolu dans Adobe Commerce 2.4.1, dont la sortie est prévue au 4e trimestre 2020.

## Lectures connexes dans notre base de connaissances de support :

* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur 404 lors de la suppression des points de récompense lors du passage en caisse multi-expédition](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
