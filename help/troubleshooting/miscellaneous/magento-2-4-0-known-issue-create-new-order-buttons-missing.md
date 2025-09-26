---
title: 'Problème connu dans Adobe Commerce 2.4.0 : boutons Créer une nouvelle commande manquants'
description: Cet article fournit une solution à un problème connu dans Commerce Admin concernant deux boutons manquants sur la page de création de commande. Lors de la création d’une commande pour un client nouveau ou existant, il n’est pas possible d’ajouter des produits à la commande à partir du catalogue, car les boutons **Ajouter des produits par SKU** et **Ajouter des produits** sont manquants. Cela est dû au fait que le regroupement JS est activé. Un correctif sera disponible dans Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Problème connu dans Adobe Commerce 2.4.0 : boutons Créer une nouvelle commande manquants

Cet article fournit une solution à un problème connu dans Commerce Admin concernant deux boutons manquants sur la page de création de commande. Lors de la création d’une commande pour un client nouveau ou existant, il n’est pas possible d’ajouter des produits à la commande à partir du catalogue, car les boutons **Ajouter des produits par SKU** et **Ajouter des produits** sont manquants. Cela est dû au fait que le regroupement JS est activé. Un correctif sera disponible dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Procédure à suivre</u>

1. Accédez à **Clients > Tous les clients**.
1. Cliquez sur le lien **Modifier** d’un client.
1. Cliquez sur le bouton **Créer une commande**.

<u>Résultat attendu</u>

Les boutons **Ajouter des produits par SKU** et **Ajouter des produits** s’affichent sur la page **Créer une commande**.

<u>Résultat réel</u>

Les boutons **Ajouter des produits par SKU** et **Ajouter des produits** sont absents de la page **Créer une commande**.

## Solution

La solution à ce problème consiste à désactiver le regroupement JS pour l’instance Adobe Commerce. Le problème devrait être résolu dans Adobe Commerce 2.4.1, dont la publication est prévue pour le 4e trimestre 2020.

## Informations connexes dans notre base de connaissances de support

* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe à l’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton « Ajouter des sélections à mon panier » ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
