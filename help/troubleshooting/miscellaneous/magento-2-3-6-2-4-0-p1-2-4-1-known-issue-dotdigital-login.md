---
title: "Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problème connu : connexion numérique"
description: Cet article décrit un problème connu d’Adobe Commerce 2.3.6, 2.4.0-p1 et 2.4.1 où il est impossible de se connecter à [dotdigital](https://dotdigital.com/) via le panneau d’administration lorsque le compte dotdigital est activé.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 : connexion numérique

Cet article décrit un problème connu d’Adobe Commerce 2.3.6, 2.4.0-p1 et 2.4.1 où il est impossible de se connecter à [dotdigital](https://dotdigital.com/) via le panneau d’administration lorsque le compte dotdigital est activé.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.6 (navigateur Safari uniquement)
* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.4.0-p1 (navigateur Safari uniquement)
* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.4.1 (navigateur Safari uniquement)

## Problème

<u>Conditions préalables</u> :

1. dotdigital account existe.
1. Des informations d’identification d’API numériques valides existent dans Adobe Commerce.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > **Configuration** > **DOTDIGITAL** > **Paramètres de conversation** > **Activé** est défini sur *Oui.*
1. Cliquez sur **Configurer** dans **Configurer le widget de conversation** ou **Configurer les équipes de discussion**.

<u>Résultats attendus</u> :

La page des paramètres de conversation doit s’ouvrir correctement via le panneau d’administration.

<u>Résultats réels</u> :

Connexion à dotdigital impossible.

## Solution

Solution : utilisez un autre navigateur que Safari pour cette situation particulière.

## Lecture connexe

[&#x200B; Problème connu d’Adobe Commerce 2.4.1 : l’adresse de sommet ne s’affichant pas avec des adresses de livraison/facturation différentes](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) dans notre base de connaissances de support.
