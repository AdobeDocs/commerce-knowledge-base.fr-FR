---
title: Recommandations de produits non affichées dans Page Builder
description: Cet article fournit une solution au problème d’affichage de l’option Recommandations de produits dans Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Recommandations de produits non affichées dans Page Builder

Cet article fournit une solution au problème d’affichage de l’option Recommandations de produits dans Page Builder.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement)

## Problème

L’option Recommandations de produits ne s’affiche pas dans Page Builder.

## Cause

Il n’existe aucune option dans Page Builder pour ajouter des recommandations de produits. Les recommandations de produits pour Page Builder sont un module facultatif qui est installé séparément.

## Solution

1. Vérifiez si vous avez installé le module séparément en exécutant la commande : `composer show magento/module-page-builder-product-recommendations`
1. S’il renvoie le message suivant : *Package magento/module-page-builder-product-recommendations introuvable*, vous devrez l’installer en exécutant la commande : `composer require magento/module-page-builder-product-recommendations`

En activant les recommandations de produits dans Page Builder, vous pourrez [ajouter une unité de recommandation](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) à tout contenu créé dans Page Builder.

## Lecture connexe

* [Ajouter du contenu - Recommandations de produits](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) dans notre guide de l’utilisateur.
* [Installez et configurez les recommandations de produits](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) dans notre documentation destinée aux développeurs.
* [Guide de l’utilisateur d’Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/user-guides/home)
