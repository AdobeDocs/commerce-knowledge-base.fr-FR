---
title: "PWA Studio : erreurs de validation lors de l’exécution du mode développeur"
description: Cette rubrique décrit une solution pour lorsque des erreurs de validation se produisent lors de l’exécution du mode développeur dans Progressive Web App (PWA) Studio for Adobe Commerce en raison de l’absence du concept de Venia (Venia est un storefront PWA). fichier d’environnement. Ce fichier contiendra les variables de votre environnement de développement local.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio : erreurs de validation lors de l’exécution du mode Développeur

Cette rubrique décrit une solution pour lorsque des erreurs de validation se produisent lors de l’exécution du mode développeur dans Progressive Web App (PWA) Studio for Adobe Commerce en raison de l’absence du concept de Venia (Venia est un storefront PWA). fichier d’environnement. Ce fichier contiendra les variables de votre environnement de développement local.

## Produits et versions concernés

* PWA Studio pour Adobe Commerce

## Problème

<u>Étape à reproduire</u>:

* Exécutez le mode Développeur dans PWA Studio pour Adobe Commerce.

<u>Résultat attendu</u>:

* Le serveur du PWA Studio démarre normalement.

<u>Résultat réel</u>:

* Vous voyez des erreurs de validation qui peuvent ressembler à :

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Cause

Le fichier de variables d’environnement pour votre environnement de développement local est manquant. Le fichier généré par la commande ci-dessous contient les variables de votre environnement de développement local.

## Solution

Assurez-vous d’exécuter la commande .

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

dans le répertoire racine afin de générer le fichier qui contiendra les variables de votre environnement de développement local.

## Lecture connexe

* [PWA Studio pour la documentation Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Venia Storefront (Concept)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
