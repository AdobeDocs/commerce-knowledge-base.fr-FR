---
title: Le produit ne s’affiche pas sur le storefront
description: Cet article fournit des solutions pour les cas où les produits ne sont pas affichés sur le storefront.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%
---
# Le produit ne s’affiche pas sur le storefront

Cet article fournit des solutions pour les cas où les produits ne sont pas affichés sur le storefront.

## Produits et versions concernés

* Adobe Commerce On-Premise X.X.X
* Adobe Commerce sur l’infrastructure cloud X.X.X

## Problème

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administration Commerce.
1. Accédez à **Catalogue** > **Produits**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Cliquez sur **Ajouter un produit** et passez par le processus de création de produit. Ou importez des produits à partir d’un fichier CSV.

<u>Résultat attendu </u> :

Le produit s’affiche sur le storefront.

<u>Résultat réel</u> :

Le produit ne s’affiche pas.

## Cause

Cela peut être dû à plusieurs raisons. Suivez les étapes ci-dessous pour vérifier les principaux points qui pourraient aider à identifier et résoudre le problème.

## Solution

Chacun des points suivants peut résoudre le problème.

* Vérifiez les paramètres du produit dans Admin. Accédez à **Catalogue** > **Produits**, ouvrez la page produit et vérifiez que les champs suivants sont correctement configurés :
  * **Activer le produit** = *Oui.*
  * **Statut des stocks** : *En stock*. Si la valeur *En rupture de stock* est correcte, assurez-vous que **Afficher les produits en rupture de stock** (**MAGASINS** > **Paramètres** > **Configuration** > **CATALOG** > **Inventory** > **Stock Options** > **Afficher les produits en rupture de stock**) est défini sur *Yes* (configuré au niveau global).
  * **Catégories** : si vous essayez de trouver le produit sur une page de catégorie, vérifiez que le produit est affecté à la catégorie. Pour simplifier la résolution des problèmes, créez une catégorie à partir de la page active et affectez-lui un produit.
  * **Visibilité** = *Catalogue, Recherche.*
  * Dans la section **Produit sur les sites web** , assurez-vous que le produit est attribué au site web approprié.
  * Basculez le sélecteur de l’étendue sur la vue du magasin où vous essayez de trouver votre produit sur le storefront, puis vérifiez les mêmes paramètres.
* Effectuez la réindexation complète en exécutant `bin/magento indexer:reindex` à partir de la console et videz tout le cache dans Admin, sous **Système** > **Outils** > **Gestion du cache**, ou à partir de la console en exécutant `bin/magento cache:clean`.
* Si ce qui précède ne vous aide pas, vous pouvez lancer une enquête plus approfondie en consultant les journaux dans le répertoire `var/log`.



