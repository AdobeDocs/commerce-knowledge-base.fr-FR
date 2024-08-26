---
title: '[!DNL Live Search] facettes non triées par ordre alphabétique'
description: Cet article fournit des informations de dépannage si les facettes  [!DNL Live Search] ne sont pas triées par ordre alphabétique.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: b20a98e44cfad6667b9fe0ab232b0020ed834ca2
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# [!DNL Live Search] facettes ne sont pas triées par ordre alphabétique

## Produits et versions concernés

Adobe Commerce versions 2.4.x et plus récentes

## Problème

Toutes les facettes de storefront Adobe Commerce sont triées par ordre alphabétique avec des options à sélection unique, quel que soit le type d’entrée affecté à l’attribut correspondant.

## Solution

Cependant, dans certains cas particuliers, les facettes peuvent ne pas être triées par ordre alphabétique comme configuré dans l’ [[!DNL Live Search] espace de travail de facettes](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace).

Pour pallier ce problème, vous pouvez trier les attributs de produit dans la section [!UICONTROL Admin] attributes .

1. Sur la barre latérale **[!UICONTROL Admin]**, accédez à **Magasins** > *Attributs* > **Produit**.
1. Sélectionnez un attribut dans le tableau.

   ![Liste d’attributs](assets/attribute-list.png)

1. Ouvrez l’attribut qui contient les valeurs à trier et sélectionnez **Attribute Information** > **Properties**.
1. Sous **Gérer les options**, vous pouvez trier les valeurs d’attribut.

   ![Attributs de tri](assets/sort-attributes.png)
