---
title: Etat de stock incorrect après installation d’Inventory management
description: Cet article fournit un correctif pour que l’état du stock soit incorrect après l’installation/la mise à niveau d’Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Etat de stock incorrect après installation d’Inventory management

Cet article fournit un correctif pour que l’état du stock soit incorrect après l’installation/la mise à niveau d’Inventory management.

## Etat du stock incorrect sur certains sites

Après l’installation ou la mise à niveau initiale pour qu’Inventory management soit installé dans l’environnement Adobe Commerce multi-site, tous les sites web n’ont pas les statuts de stock corrects pour les produits.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions, avec Inventory management installé
* Adobe Commerce On-Premise 2.3.0 et versions ultérieures, avec Inventory management installé
* Magento Open Source 2.3.0 et versions ultérieures, avec Inventory management installé

## Cause

Lors de la première installation/mise à niveau, tous vos produits sont attribués à la source par défaut, ce qui associe toutes les quantités à cette source. Le Source par défaut est affecté au stock par défaut, le site web par défaut étant associé.

## Solution

Si vous disposez de plusieurs sites web, vous devez les ajouter en tant que Sales Channel aux actions par défaut ou aux autres actions personnalisées.

Consultez la section [Stock du guide de l’utilisateur/du wiki](https://docs.magento.com/m2/ce/user_guide/catalog/inventory-stock.html) dans notre guide de l’utilisateur pour plus d’informations sur la façon de procéder.
