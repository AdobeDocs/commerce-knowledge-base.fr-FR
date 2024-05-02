---
title: Recommendations de produit ne s’affiche pas dans le créateur de pages
description: Cet article fournit une solution au problème où l’option Recommendations de produit n’est pas affichée dans le créateur de pages.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Recommendations de produit ne s’affiche pas dans le créateur de pages

Cet article fournit une solution au problème où l’option Recommendations de produit n’est pas affichée dans le créateur de pages.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement)

## Problème

Option Recommendations du produit ne s’affichant pas dans le Créateur de pages.

## Cause

Il n’existe pas d’option dans le Créateur de pages pour ajouter le Recommendations de produit. Le Recommendations de produit pour Page Builder est un module facultatif qui est installé séparément.

## Solution

1. Vérifiez si vous avez installé le module séparément en exécutant la commande : `composer show magento/module-page-builder-product-recommendations`
1. S’il renvoie le message suivant : *Magento/module-page-builder-product-recommendations introuvable*, vous devez l’installer en exécutant la commande : `composer require magento/module-page-builder-product-recommendations`

En activant le Recommendations de produit dans le créateur de pages, vous pourrez [ajouter une unité de recommandation](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) à tout contenu créé dans le Créateur de pages.

## Lecture connexe

* [Ajouter du contenu - Recommendations de produit](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) dans notre guide d’utilisation.
* [Installation et configuration de Recommendations de produit](https://devdocs.magento.com/recommendations/install-configure.html) dans notre documentation destinée aux développeurs.
* [Guide de l’utilisateur d’Adobe Commerce](https://docs.magento.com/user-guide/)
