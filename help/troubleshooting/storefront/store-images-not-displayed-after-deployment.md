---
title: Stocker les images non affichées après le déploiement
description: Cet article fournit une solution pour les images qui ne s’affichent pas correctement après le déploiement.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Stocker les images non affichées après le déploiement

Cet article fournit une solution pour les images qui ne s’affichent pas correctement après le déploiement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

Lorsque vous utilisez un thème storefront avec redimensionnement d’image, les images ne s’affichent pas ou ne disparaissent pas des pages du catalogue lors du déploiement.

## Cause

Cela peut se produire en raison du chargement des images à partir du cache.

## Solution

Si cela se produit, vous pouvez utiliser la commande du Magento pour régénérer le cache des images et afficher correctement les images.

Pour ce faire, vous avez besoin des informations SSH et de l’URL de stockage disponibles via le [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH à votre projet qui était une source pour [vidage de base de données](/help/how-to/general/create-database-dump-on-cloud.md), comme décrit dans [SSH vers l’environnement](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) dans notre documentation destinée aux développeurs.
1. Régénérez le cache d’image en exécutant :

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Testez les pages de catégorie via l’URL du magasin.
