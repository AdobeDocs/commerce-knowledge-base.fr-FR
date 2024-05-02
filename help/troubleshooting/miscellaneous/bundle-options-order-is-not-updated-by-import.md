---
title: L’ordre des options de bundle n’est pas mis à jour par import
description: Cet article fournit une solution au problème lorsque, après l’importation de produits à partir d’un fichier .csv, les options de produit du bundle apparaissent dans un ordre différent de celui qui est répertorié dans le fichier d’importation.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# L’ordre des options de bundle n’est pas mis à jour par import

Cet article fournit une solution au problème lorsque, après l’importation de produits à partir d’un fichier .csv, les options de produit du bundle apparaissent dans un ordre différent de celui qui est répertorié dans le fichier d’importation.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source

## Problème

<u>Conditions préalables</u>:

Vous disposez d’un fichier .csv valide contenant des produits de bundle.

<u>Étapes à reproduire</u>:

1. Importez le fichier à l’aide du [Fonctionnalité d’importation](https://docs.magento.com/m2/ee/user_guide/system/data-import.html).
1. Ouvrez la page du produit du bundle.

<u>Résultats attendus</u>:

L’ordre des options est le même que dans le fichier .csv .

<u>Résultats réels</u>:

L’ordre des options diffère de celui du fichier .csv .

## Cause

La position des options n’a pas été déclarée explicitement.

## Solution

1. Déclarez explicitement une position pour chaque option dans la variable `position` du paramètre `bundle_values` dans le fichier .csv. Pour obtenir des instructions détaillées, voir [Modifier les données du produit](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data) dans notre guide d’utilisation.
1. Répétez l&#39;opération d&#39;import.

Pour obtenir des informations générales sur l’importation, voir [Importation d’un produit groupé](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html) dans notre guide d’utilisation.
