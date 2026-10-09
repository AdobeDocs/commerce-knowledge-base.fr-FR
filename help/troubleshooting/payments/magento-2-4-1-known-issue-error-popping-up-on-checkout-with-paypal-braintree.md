---
title: 'Problème connu dans Adobe Commerce 2.4.1 : une erreur s’affiche lors de la passage en caisse avec PayPal Braintree'
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1, où un message d’erreur s’affiche et disparaît à l’étape Facturation du passage en caisse si le paiement Braintree PayPal est utilisé et que l’expédition de plusieurs adresses est sélectionnée.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
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
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%
---
# Problème connu dans Adobe Commerce 2.4.1 : une erreur s’affiche lors de la passage en caisse avec PayPal Braintree

Cet article décrit un problème connu d’Adobe Commerce 2.4.1, où un message d’erreur s’affiche et disparaît à l’étape Facturation du passage en caisse si le paiement Braintree PayPal est utilisé et que l’expédition de plusieurs adresses est sélectionnée.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.4.1
* Adobe Commerce on-premise 2.4.1

## Problème

Un message d&#39;erreur apparaît et disparaît à l&#39;étape Facturation du passage en caisse si le paiement PayPal Braintree est utilisé et que l&#39;expédition de plusieurs adresses est sélectionnée.

<u>Procédure à suivre :</u>

1. Sur le storefront, connectez-vous en tant que client (il peut éventuellement s’agir d’un passage en caisse des invités, s’il est activé dans Admin).
1. Ajoutez un produit au panier.
1. Cliquez pour ouvrir l’aperçu du panier.
1. Cliquez sur **Afficher et modifier le panier**.
1. Sur la page Panier, cliquez sur **Extraire avec plusieurs adresses**.
1. Cliquez sur **Accéder aux informations d’expédition** et indiquez les adresses.
1. Cliquez sur **Continuer vers les informations de facturation**.
1. Sélectionnez **PayPal Braintree** et cliquez sur le bouton **PayPal**.
1. Dans la fenêtre pop-up, cliquez sur **Accepter et payer**.

<u>Résultat attendu : </u>

La commande est passée sans erreur.

<u>Résultat réel :</u>

La commande est passée, mais avec une erreur. Impossible d&#39;initialiser le paiement *PayPal). Veuillez contacter le propriétaire du magasin*.  L’erreur s’affiche pendant une seconde et disparaît.

## Correctif

Puisque le placement des commandes n’est pas bloqué, il n’est pas nécessaire d’effectuer des étapes de contournement.
