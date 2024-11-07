---
title: Recommendations de produit ne s’affiche pas dans le créateur de pages
description: Cet article fournit une solution au problème où l’option Recommendations de produit n’est pas affichée dans le créateur de pages.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
1. S&#39;il renvoie le message suivant : *Magento/module-page-builder-product-recommendations introuvable*, vous devrez l&#39;installer en exécutant la commande : `composer require magento/module-page-builder-product-recommendations`

En activant le Recommendations de produit dans le créateur de pages, vous pourrez [ajouter une unité de recommandation](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) à tout contenu créé dans le créateur de pages.

## Lecture connexe

* [Ajouter du contenu - Recommendations produit](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) dans notre guide d’utilisation.
* [Installez et configurez le produit Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) dans notre documentation destinée aux développeurs.
* [Guide de l’utilisateur Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/user-guides/home)
