---
title: Statut de produit incorrect lors de la création par programmation
description: Cet article fournit un correctif pour les cas où le statut du produit est Désactivé et où les produits ne sont pas affichés en vitrine ou sont affectés à de mauvaises vues de boutique, lors de leur création/mise à jour par programmation.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%
---
# Statut de produit incorrect lors de la création par programmation

Cet article fournit un correctif pour les cas où le statut du produit est Désactivé et où les produits ne sont pas affichés en vitrine ou sont affectés à de mauvaises vues de boutique, lors de leur création/mise à jour par programmation.

## Produits et versions concernés

* Adobe Commerce sur Cloud Infrastructure 2.X.X
* Adobe Commerce On-Premise 2.X.X

## Problème

Lorsque les produits du catalogue sont créés ou mis à jour par programmation à partir d’un script avec l’application Adobe Commerce amorcée, les produits peuvent avoir le statut Désactivé et/ou être affectés aux mauvaises vues de magasin.

## Cause

Le problème peut se produire en raison des restrictions de liste de contrôle d’accès définies pour les rôles d’administration des instances Adobe Commerce. Dans le cas d&#39;une application amorcée, il n&#39;y aura aucune session d&#39;administrateur initialisée avec les paramètres ACL appropriés. Cela entraînerait l’échec des validations dans le module `Magento_AdminGws`, qui est responsable de la vérification des autorisations sur de telles actions.

## Solution pour un statut de produit incorrect

Définissez une préférence d’ID dynamique pour le `Magento\Framework\Authorization\PolicyInterface`, comme décrit dans la rubrique [ObjectManager>Mises à jour programmatiques du produit](https://developer.adobe.com/commerce/php/development/components/object-manager/) dans notre documentation destinée aux développeurs.

## Lecture connexe

* [Github : impossible de modifier le statut du produit créé avec productRepository](https://github.com/magento/magento2/issues/5664)
