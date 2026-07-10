---
title: Colonne de statut Adobe Commerce manquante dans le fichier CSV des produits exportés
description: Cet article fournit une solution au problème d’introuvabilité de la colonne de statut dans le fichier CSV contenant les produits exportés.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Colonne de statut Adobe Commerce manquante dans le fichier CSV des produits exportés

Cet article fournit une solution au problème d’absence de colonne de statut (indiquant par exemple si le produit est activé ou désactivé) dans le fichier CSV contenant les produits exportés. Le statut du produit est indiqué par la colonne [!UICONTROL product_online] .

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Vous ne parvenez pas à localiser la colonne [!UICONTROL status] dans le fichier CSV contenant les produits exportés. Ainsi, par exemple, vous exportez un fichier CSV de tous les SKU, avec leur statut, mais le tableau semble ne pas contenir la colonne [!UICONTROL status].

<u>Procédure à suivre :</u>

1. Dans Adobe Commerce Admin, sélectionnez **[!UICONTROL System]**, sous **[!UICONTROL Data Transfer]** sélectionnez **[!UICONTROL Export]**.
1. Dans la section **[!UICONTROL Export Settings]** , sélectionnez dans la **[!UICONTROL Products]** déroulante **[!UICONTROL Entity Type]** .
1. Recherchez **[!UICONTROL status]**, répertorié sous **[!UICONTROL Attribute Code]**. Ce code d’attribut apparaît dans la liste des attributs disponibles (**[!UICONTROL Enable Product]**).
1. Cliquez sur **[!UICONTROL Export]**.

<u>Résultat attendu : </u>

Dans le fichier CSV que vous venez d’exporter, une colonne intitulée [!UICONTROL status] s’affiche.

<u>Résultat réel :</u>

Aucune colonne intitulée [!UICONTROL status] n’apparaît dans le fichier CSV exporté.

## Cause

L’attribut status du produit a été renommé dans le fichier CSV. Il s’agit désormais de la colonne [!UICONTROL product_online] .

## Solution

1. Sélectionnez **[!UICONTROL System]**, sous **[!UICONTROL Data Transfer]** sélectionnez **[!UICONTROL Import]**.
1. Cliquez sur **[!UICONTROL Download Sample File]**.
1. La colonne [!UICONTROL product_online] s’affiche dans le fichier CSV.

## Lecture connexe

* [Utilisation de fichiers CSV](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-csv) dans notre guide de l’utilisateur.
* [Référence des attributs d’exportation de produit](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-attributes-product) dans notre guide de l’utilisateur.
