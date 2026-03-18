---
title: 'PWA Studio : erreurs de validation lors de l’exécution du mode Développeur'
description: Cette rubrique présente une solution pour les erreurs de validation qui se produisent lors de l’exécution du mode développeur dans Progressive Web App (PWA) Studio pour Adobe Commerce, car le fichier d’environnement venia-concept (Venia est un storefront PWA) n’a pas été créé auparavant. Ce fichier contient les variables de votre environnement de développement local.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 9d32a5971341ed8dc46e0932c10eaac4d17ec299
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio : erreurs de validation lors de l’exécution du mode Développeur

Cette rubrique présente une solution pour les erreurs de validation qui se produisent lors de l’exécution du mode développeur dans Progressive Web App (PWA) Studio pour Adobe Commerce, car le fichier d’environnement venia-concept (Venia est un storefront PWA) n’a pas été créé auparavant. Ce fichier contient les variables de votre environnement de développement local.

## Produits et versions concernés

* PWA Studio pour Adobe Commerce

## Problème

<u>Étape à reproduire</u> :

* Exécutez le mode Développeur dans PWA Studio pour Adobe Commerce.

<u>Résultat attendu </u> :

* Le serveur PWA Studio démarre normalement.

<u>Résultat réel</u> :

* Des erreurs de validation s’affichent, qui peuvent ressembler à ce qui suit :

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Cause

Le fichier de variables d’environnement pour votre environnement de développement local est manquant. Le fichier généré par la commande ci-dessous contient les variables de votre environnement de développement local.

## Solution

Veillez à exécuter la commande .

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

dans le répertoire racine afin de générer le fichier qui contiendra les variables de votre environnement de développement local.

## Lecture connexe

* [Documentation PWA Studio for Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Venia Storefront (Concept)](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
