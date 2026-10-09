---
title: 'Adobe Commerce 2.4.0 : erreur de passage en caisse lors de la sélection des paiements locaux'
description: 'Cet article présente une solution à un problème connu dans Adobe Commerce lors du passage en caisse, où un message d’erreur s’affiche lors de la sélection d’un mode de paiement local pour certains pays. Cela se produit pour les pays suivants : Belgique, Italie, Pays-Bas, Pologne et Espagne.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0 : erreur de passage en caisse lors de la sélection des paiements locaux

Cet article présente une solution à un problème connu dans Adobe Commerce lors du passage en caisse, où un message d’erreur s’affiche lors de la sélection d’un mode de paiement local pour certains pays. Cela se produit pour les pays suivants : Belgique, Italie, Pays-Bas, Pologne et Espagne.

Message d’erreur « *Il n’existe actuellement aucun mode de paiement disponible. Veuillez mettre à jour votre adresse de facturation.* » apparaîtra, mais les modes de paiement locaux apparaîtront toujours et fonctionneront correctement. Un correctif permanent sera disponible dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables</u> :

* Adobe Commerce 2.4.0 est installé.
* Créez un produit et une catégorie.
* Configurez [Mode De Paiement &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Procédure à suivre </u> :

1. Accédez au storefront.
1. Sélectionnez les articles à ajouter au panier.
1. Passer en caisse.
1. Remplissez le formulaire d’adresse avec une adresse valide.
1. Accédez à la page Révision et paiements.

<u>Résultat attendu </u> :

Les modes de paiement locaux doivent être affichés normalement, sans message d&#39;erreur.

<u>Résultat réel</u> :

Message d’erreur « *Il n’existe actuellement aucun mode de paiement disponible. Veuillez mettre à jour votre adresse de facturation.* » apparaît, mais les modes de paiement locaux s&#39;afficheront toujours et fonctionneront correctement.

## Solution

La solution consiste à ignorer le message d&#39;erreur affiché et à continuer le paiement comme d&#39;habitude, car tous les modes de paiement locaux fonctionneront normalement. Le correctif était disponible à partir de la version 2.4.1 d’Adobe Commerce.

## Lecture connexe

* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
