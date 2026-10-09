---
title: '[!DNL Live Search] facettes ne sont pas triées par ordre alphabétique'
description: Cet article fournit des informations de dépannage si les facettes [!DNL Live Search] ne sont pas triées par ordre alphabétique.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%
---
# [!DNL Live Search] facettes ne sont pas triées par ordre alphabétique

## Produits et versions concernés

Adobe Commerce versions 2.4.x et ultérieures

## Problème

Toutes les facettes de storefront Adobe Commerce sont triées par ordre alphabétique avec des options à sélection unique, quel que soit le type d’entrée affecté à l’attribut correspondant.

## Solution

Cependant, dans certains cas, les facettes ne sont pas triées par ordre alphabétique comme configuré dans l’espace de travail [[!DNL Live Search] Facettisation](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace).

Pour pallier ce problème, vous pouvez trier les attributs de produit dans la section attributs de [!UICONTROL Admin] .

1. Sur la barre latérale **[!UICONTROL Admin]**, accédez à **Magasins** > *Attributs* > **Produit**.
1. Sélectionnez un attribut dans le tableau.

   ![Liste d’attributs](assets/attribute-list.png)

1. Ouvrez l’attribut qui contient les valeurs à trier et sélectionnez **Informations sur l’attribut** > **Propriétés**.
1. Sous **Gérer les options**, vous pouvez trier les valeurs d’attribut.

   ![Attributs de tri](assets/sort-attributes.png)
