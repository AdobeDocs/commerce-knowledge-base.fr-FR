---
title: 'Adobe Commerce 2.4.0, 2.4.1 : activer la facture partielle Braintree Venmo'
description: Cet article décrit un problème Adobe Commerce 2.4.0 et 2.4.1 connu, où la facturation partielle n’est pas disponible pour les commandes passées à l’aide de Braintree via Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---
# Adobe Commerce 2.4.0, 2.4.1 : activer la facture partielle Braintree Venmo

Cet article décrit un problème Adobe Commerce 2.4.0 et 2.4.1 connu, où la facturation partielle n’est pas disponible pour les commandes passées à l’aide de Braintree via Venmo.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0 et 2.4.1
* Adobe Commerce sur les infrastructures cloud 2.4.0 et 2.4.1

## Problème

<u>Conditions préalables : </u>

Dans la configuration du mode de paiement Braintree, définissez **Activer Venmo via Braintree** = *Oui* avec **Action de paiement** = *Autorisation* ; **Activer Vault pour les paiements par carte** = *No*.

<u>Procédure à suivre :</u>

1. Créez une commande pour deux produits ou plus, en utilisant Venmo (Braintree) comme mode de paiement.
1. Ouvrez la commande dans Commerce Admin.
1. Créez une facture pour l&#39;un des produits commandés.
1. Essayez de créer une facture pour les autres produits commandés.

<u>Résultat attendu : </u>

Facture créée.

<u>Résultat réel :</u>

Le message d’erreur suivant s’affiche : *La commande « vault\_capture » n’existe pas. Vérifiez la commande et réessayez.*

## Solution

Capturez le montant total lors de la création de factures pour les commandes passées à l’aide de Braintree via Venmo.
