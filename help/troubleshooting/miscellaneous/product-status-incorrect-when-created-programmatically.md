---
title: Etat du produit incorrect lors de la création programmée
description: Cet article fournit un correctif lorsque l’état du produit est Désactivé et que les produits ne sont pas affichés au premier plan du magasin ou sont affectés aux mauvaises vues du magasin, lorsqu’ils sont créés/mis à jour par programmation.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Etat du produit incorrect lors de la création programmée

Cet article fournit un correctif lorsque l’état du produit est Désactivé et que les produits ne sont pas affichés au premier plan du magasin ou sont affectés aux mauvaises vues du magasin, lorsqu’ils sont créés/mis à jour par programmation.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.X.X
* Adobe Commerce On-Premise 2.X.X

## Problème

Lorsque les produits du catalogue sont créés ou mis à jour par programmation à partir d’un script avec l’application Adobe Commerce démarrée, les produits peuvent avoir l’état Désactivé et/ou être affectés aux mauvaises vues de magasin.

## Cause

Le problème peut apparaître en raison des restrictions d’ACL définies pour les rôles d’administrateur d’instance Adobe Commerce. Dans le cas d’une application amorcée, il n’y aura aucune session d’administration initialisée avec les paramètres ACL appropriés. Cela provoquerait l’échec des validations dans le module `Magento_AdminGws`, qui est responsable du contrôle des autorisations sur ces actions.

## Solution pour un état de produit incorrect

Définissez une préférence d’ID dynamique pour `Magento\Framework\Authorization\PolicyInterface`, comme décrit dans la rubrique [ObjectManager>Mises à jour de produit programmatiques](https://developer.adobe.com/commerce/php/development/components/object-manager/) de notre documentation destinée aux développeurs.

## Lecture connexe

* [Github : impossible de modifier l’état du produit créé avec productRepository](https://github.com/magento/magento2/issues/5664)
