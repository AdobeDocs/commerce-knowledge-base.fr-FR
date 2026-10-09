---
title: Modules manquants dans Adobe Commerce 2.4.4
description: Cet article fournit une solution au problème lorsque les modules inclus dans les versions précédentes d’Adobe Commerce ne sont pas présents dans la version 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# Modules manquants dans Adobe Commerce 2.4.4

Cet article fournit une solution lorsque les modules inclus dans les versions précédentes d’Adobe Commerce ne sont pas présents dans la version 2.4.4.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Vous ne pouvez pas installer de module tiers ou vous avez constaté que certaines des extensions groupées de base ne sont pas présentes lorsque vous avez effectué la mise à niveau vers Adobe Commerce 2.4.4. Cela ne doit résulter de l’installation d’un module tiers qui nécessite l’une des extensions groupées supprimées d’Adobe Commerce 2.4.4 ou si le projet utilise certaines des fonctionnalités de l’un des modules supprimés.

* Scénario 1 : le projet a utilisé l’une des fonctionnalités du module principal groupé. Le module groupé utilisé n’est pas inclus dans Adobe Commerce 2.4.4. Après la mise à niveau vers Adobe Commerce 2.4.4, vous réalisez que le module et ses fonctionnalités sont manquants.

* Scénario 2 : un module installé dans votre projet actuel possède une dépendance sur l’un des modules groupés supprimés.

Ce comportement est attendu, car les extensions groupées par fournisseur ont été supprimées de la base de code d’Adobe Commerce 2.4.4.

## Solution

Installez/achetez les extensions officielles séparément. Ils sont disponibles sur [&#128279;](https://marketplace.magento.com/extensions.html).

## Lecture connexe

[Extensions groupées par fournisseur](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) dans Documentation Adobe Commerce > Informations sur les versions > Notes de mise à jour d’Adobe Commerce 2.4.4.
