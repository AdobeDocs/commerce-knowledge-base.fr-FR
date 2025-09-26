---
title: 'Problème connu d’Adobe Commerce 2.4.0 : libellé « Remboursement » manquant dans Klarna'
description: Cet article fournit une solution à un problème connu dans Admin en raison d’un libellé **Remboursement** manquant dans Klarna VBE (extension groupée avec le fournisseur). Lorsque vous vous trouvez sur le portail Klarna pour effectuer un remboursement, l'étiquette **Remboursement** n'est pas affichée à côté du produit groupé qui a été remboursé.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '390'
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

* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe à l’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton « Ajouter des sélections à mon panier » ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
