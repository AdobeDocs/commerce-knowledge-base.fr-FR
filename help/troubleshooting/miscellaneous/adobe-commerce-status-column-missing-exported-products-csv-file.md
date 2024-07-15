---
title: Colonne d’état Adobe Commerce absence de fichier CSV de produits exportés
description: Cet article fournit une solution au problème lorsque vous ne pouvez pas localiser la colonne d’état dans le fichier CSV contenant les produits exportés.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Colonne d’état Adobe Commerce absence de fichier CSV de produits exportés

Cet article fournit une solution au problème lorsque vous ne pouvez pas localiser la colonne d’état (c’est-à-dire indiquer si le produit est activé ou désactivé) dans le fichier CSV contenant les produits exportés. L’état du produit est indiqué par la colonne [!UICONTROL product_online].

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Vous ne pouvez pas localiser la colonne [!UICONTROL status] dans le fichier CSV contenant les produits exportés. Ainsi, par exemple, vous exportez un fichier CSV de tous les SKU, avec leur état, mais le tableau semble ne pas contenir la colonne [!UICONTROL status].

<u>Étapes à reproduire :</u>

1. Dans l’administrateur Adobe Commerce, sélectionnez **[!UICONTROL System]**, sous **[!UICONTROL Data Transfer]** sélectionnez **[!UICONTROL Export]**.
1. Dans la section **[!UICONTROL Export Settings]** , sélectionnez dans la liste déroulante **[!UICONTROL Entity Type]** **[!UICONTROL Products]**.
1. Recherchez **[!UICONTROL status]**, répertorié sous **[!UICONTROL Attribute Code]**. Ce code d’attribut s’affiche dans la liste des attributs disponibles (**[!UICONTROL Enable Product]**).
1. Cliquez sur **[!UICONTROL Export]**.

<u>Résultat attendu :</u>

Dans le fichier CSV que vous venez d’exporter, une colonne intitulée [!UICONTROL status] s’affiche.

<u>Résultat réel :</u>

Une colonne intitulée [!UICONTROL status] ne s’affiche pas dans le fichier csv exporté.

## Cause

L’attribut d’état du produit a été renommé dans le fichier CSV. Il s’agit désormais de la colonne [!UICONTROL product_online].

## Solution

1. Sélectionnez **[!UICONTROL System]**, sous **[!UICONTROL Data Transfer]** sélectionnez **[!UICONTROL Import]**.
1. Cliquez sur **[!UICONTROL Download Sample File]**.
1. Vous pouvez voir la colonne [!UICONTROL product_online] dans le fichier CSV.

## Lecture connexe

* [Utilisation de fichiers CSV](https://docs.magento.com/user-guide/system/data-csv.html) dans notre guide d’utilisation.
* [Référence des attributs d’exportation de produits](https://docs.magento.com/user-guide/system/data-attributes-product.html) dans notre guide d’utilisation.
