---
title: Stocker les images non affichées après le déploiement
description: Cet article fournit une solution lorsque les images ne s’affichent pas correctement après le déploiement.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# Stocker les images non affichées après le déploiement

Cet article fournit une solution lorsque les images ne s’affichent pas correctement après le déploiement.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.2.x, 2.3.x

## Problème

Lorsque vous utilisez un thème de storefront avec le redimensionnement de l’image, les images ne s’affichent pas ou ne disparaissent pas des pages du catalogue lors du déploiement.

## Cause

Cela peut se produire en raison du chargement des images à partir du cache.

## Solution

Si cela se produit, vous pouvez utiliser la commande Magento pour régénérer le cache d’images et afficher correctement les images.

Pour ce faire, vous avez besoin des informations SSH et de l’URL du magasin disponibles via [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr).

1. SSH vers votre projet qui était une source pour l’[image mémoire de la base de données](/help/how-to/general/create-database-dump-on-cloud.md), comme décrit dans [SSH vers l’environnement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections) dans notre documentation destinée aux développeurs.
1. Régénérez le cache d’images en exécutant :

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Testez les pages de catégorie via l’URL du magasin.
