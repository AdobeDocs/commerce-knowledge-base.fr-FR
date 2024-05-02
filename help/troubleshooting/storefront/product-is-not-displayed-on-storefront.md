---
title: Le produit ne s’affiche pas sur le storefront
description: Cet article fournit des solutions pour les cas où les produits ne sont pas affichés sur le storefront.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Le produit ne s’affiche pas sur le storefront

Cet article fournit des solutions pour les cas où les produits ne sont pas affichés sur le storefront.

## Produits et versions concernés

* Adobe Commerce sur site X.X.X
* Adobe Commerce sur l’infrastructure de cloud X.X.X

## Problème

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Catalogue** > **Produits**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Cliquez sur **Ajouter un produit** et suivez le processus de création du produit. Vous pouvez également importer des produits à partir d’un fichier CSV.

<u>Résultat attendu</u>:

Le produit s’affiche sur le storefront.

<u>Résultat réel</u>:

Le produit ne s’affiche pas.

## Cause

Cela peut être dû à un certain nombre de raisons. Veuillez suivre les étapes ci-dessous pour vérifier les principaux points qui pourraient aider à identifier et résoudre le problème.

## Solution

Chacun des points suivants peut résoudre le problème.

* Vérifiez les paramètres du produit dans Admin. Accédez à **Catalogue** > **Produits**, ouvrez la page produit et assurez-vous que les champs suivants sont correctement configurés :
   * **Activer le produit** = *Oui.*
   * **État du stock**: *En stock*. Ou si *En rupture de stock* est la valeur correcte, assurez-vous que la variable **Afficher les produits en rupture de stock** (**MAGASINS** > **Paramètres** > **Configuration** > **CATALOGUE** > **Inventaire** > **Options Stock** > **Afficher les produits en rupture de stock**) est défini sur *Oui* (configuré au niveau global).
   * **Catégories**: si vous essayez de trouver le produit sur une page de catégorie, vérifiez que le produit est affecté à la catégorie. Pour simplifier le dépannage, créez une catégorie à partir de la page active et affectez-lui un produit.
   * **Visibilité** = *Catalogue, Recherche.*
   * Dans le **Produit sur les sites web** , assurez-vous que le produit est affecté au site web approprié.
   * Basculez le sélecteur de portée vers la vue de magasin où vous essayez de trouver votre produit sur le storefront et vérifiez les mêmes paramètres.
* Effectuez la réindexation complète en exécutant `bin/magento indexer:reindex` à partir de la console et videz tout le cache dans l’Admin, sous **Système** > **Outils** > **Gestion du cache** ou à partir de la console en exécutant `bin/magento cache:clean`.
* Si ce qui précède ne vous aide pas, vous pouvez lancer une enquête plus approfondie en vérifiant les journaux dans la variable `var/log` répertoire .

## Lecture connexe dans notre base de connaissances de soutien

* [Emplacements des journaux (répertoires) pour l’architecture Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Emplacements des logs (répertoires) pour l’architecture de démarrage](/help/how-to/general/log-locations-directories-for-starter-plan.md)
