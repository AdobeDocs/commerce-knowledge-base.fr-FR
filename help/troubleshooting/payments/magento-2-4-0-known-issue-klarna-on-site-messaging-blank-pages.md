---
title: 'Problème connu dans Adobe Commerce 2.4.0 : pages vierges de la messagerie sur site Klarna'
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.0 avec la méthode de paiement Klarna, en raison duquel l’activation de la messagerie sur site Klarna sans spécifier de thème de conception, entraîne l’affichage incorrect des pages de produits sur le storefront (les pages de produits apparaissent vides).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%
---
# Problème connu dans Adobe Commerce 2.4.0 : pages vierges de la messagerie sur site Klarna

Cet article décrit un problème connu d’Adobe Commerce 2.4.0 avec la méthode de paiement Klarna, en raison duquel l’activation de la messagerie sur site Klarna sans spécifier de thème de conception, entraîne l’affichage incorrect des pages de produits sur le storefront (les pages de produits apparaissent vides).

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

<u>Conditions préalables : </u> méthode de paiement Klarna est activée.

<u>Procédure à suivre :</u>

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **Ventes** > **Modes de paiement** > **Klarna** > **Klarna Messagerie sur site**.
1. Définissez **Activer** sur *Oui*.
1. Laissez le champ **Thème de conception** vide.
1. Enregistrez la configuration en cliquant sur **Enregistrer la configuration**.
1. Accédez au storefront et à n’importe quelle page de produit.

<u>Résultat attendu : </u>

La page se charge correctement avec le thème de conception par défaut appliqué à la messagerie sur site Klarna.

<u>Résultat réel :</u>

Une page vierge s’affiche.

## Solution

Si vous activez la messagerie sur site Klarna, assurez-vous toujours que le champ **Thème de conception** n’est pas vide.
