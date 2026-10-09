---
title: 'Problème connu d’Adobe Commerce 2.4.0 : libellé « Remboursement » manquant dans Klarna'
description: Cet article fournit une solution à un problème connu dans Admin en raison d’un libellé **Remboursement** manquant dans Klarna VBE (extension groupée avec le fournisseur). Lorsque vous vous trouvez sur le portail Klarna pour effectuer un remboursement, l'étiquette **Remboursement** n'est pas affichée à côté du produit groupé qui a été remboursé.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
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
source-wordcount: '332'
ht-degree: 0%
---
# Problème connu d’Adobe Commerce 2.4.0 : libellé « Remboursement » manquant dans Klarna

Cet article fournit une solution à un problème connu dans Admin en raison d’un libellé **Remboursement** manquant dans Klarna VBE (extension groupée avec le fournisseur). Lorsque vous vous trouvez sur le portail Klarna pour effectuer un remboursement, l&#39;étiquette **Remboursement** n&#39;est pas affichée à côté du produit groupé qui a été remboursé.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables : </u>

* Klarna est activé.
* Un produit groupé est créé.

<u>Procédure à suivre</u>

1. Accédez au serveur frontal Adobe Commerce et ajoutez un Produit groupé au **panier**.
1. Accédez à l’extraction.
1. Saisissez les informations du client dans le passage en caisse et cliquez sur **Suivant**.
1. Sélectionnez **option KP** et cliquez sur **Passer une commande**.
1. Accédez à **Admin** > **Ventes** > **Commandes**.
1. Ouvrez la commande.
1. Créer une facture pour le produit.
1. Accédez à **Factures** > **Sélectionner une facture** > Cliquez sur **Avoir** > Cliquez sur **Rembourser** (et non **Rembourser hors ligne**).
1. Accédez au portail Klarna.
1. Ouvrez la commande.
1. Le libellé **Remboursement** est présent.

<u>Résultat attendu</u>

Sur le portail Klarna, l&#39;étiquette **Remboursement** est affichée à côté du produit qui a été remboursé.

<u>Résultat réel</u>

Sur le portail Klarna, l&#39;étiquette **Remboursement** n&#39;est pas affichée à côté du produit qui a été remboursé.

## Solution

La solution à ce problème consiste à ignorer l’étiquette **Remboursement** manquante dans le portail Klarna pour les produits groupés remboursés. Le remboursement a eu lieu, même si l’étiquette **Remboursement** ne s’affichait pas. Le problème devrait être résolu dans Adobe Commerce 2.4.1, dont la publication est prévue pour le 4e trimestre 2020.

## Informations connexes dans notre base de connaissances de support :

* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
