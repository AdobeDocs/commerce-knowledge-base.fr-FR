---
title: 'Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problème connu : dotdigital login'
description: Cet article décrit un problème connu d’Adobe Commerce 2.3.6, 2.4.0-p1 et 2.4.1 en raison duquel il est impossible de se connecter à [dotdigital](https://dotdigital.com/) via le panneau d’administration lorsque le compte dotdigital est activé.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 38b4d310cab9dccad142c244f6e07f8421a9894d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problème connu : dotdigital login

Cet article décrit un problème connu d’Adobe Commerce 2.3.6, 2.4.0-p1 et 2.4.1 en raison duquel il est impossible de se connecter à [dotdigital](https://dotdigital.com/) via le panneau d’administration lorsque le compte dotdigital est activé.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce on-premise 2.3.6 (navigateur Safari uniquement)
* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce On-Premise 2.4.0-p1 (navigateur Safari uniquement)
* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce on-premise 2.4.1 (navigateur Safari uniquement)

## Problème

<u>Conditions préalables</u> :

1. le compte dotdigital existe.
1. Il existe des informations d’identification d’API dotdigital valides dans Adobe Commerce.

<u>Procédure à suivre </u> :

1. Accédez à **Magasins** > **Configuration** > **DOTDIGITAL** > **Paramètres de conversation** > **Activé** est défini sur *Yes.*
1. Cliquez sur **Configurer** dans **Configurer le widget de conversation** ou **Configurer les équipes de conversation**.

<u>Résultats attendus</u> :

La page des paramètres de conversation doit s’ouvrir correctement via le panneau d’administration.

<u>Résultats réels</u> :

Connexion à dotdigital impossible.

## Solution

Solution : utilisez un autre navigateur que Safari dans ce cas particulier.