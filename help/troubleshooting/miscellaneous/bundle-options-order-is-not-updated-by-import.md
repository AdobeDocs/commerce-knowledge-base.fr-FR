---
title: L’ordre des options de bundle n’est pas mis à jour par import
description: Cet article fournit une solution au problème lorsque, après l’importation de produits à partir d’un fichier .csv, les options de produit du bundle apparaissent dans un ordre différent de celui qui est répertorié dans le fichier d’importation.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

<u>Conditions préalables</u> :

Vous disposez d’un fichier .csv valide contenant des produits de bundle.

<u>Étapes à reproduire</u> :

1. Importez le fichier à l’aide de la [fonctionnalité d’importation](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Ouvrez la page du produit du bundle.

<u>Résultats attendus</u> :

L’ordre des options est le même que dans le fichier .csv .

<u>Résultats réels</u> :

L’ordre des options diffère de celui du fichier .csv .

## Cause

La position des options n’a pas été déclarée explicitement.

## Solution

1. Déclarez explicitement une position pour chaque option dans le paramètre `position` de la colonne `bundle_values` du fichier .csv. Pour obtenir des instructions détaillées, voir [Modifier les données du produit](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) dans notre guide d’utilisation.
1. Répétez l&#39;opération d&#39;import.

Pour obtenir des informations générales sur l’importation, consultez la section [Importation de produit groupé](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products) de notre guide d’utilisation.
