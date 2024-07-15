---
title: Modules manquants dans Adobe Commerce 2.4.4
description: Cet article fournit une solution au problème lorsque les modules inclus dans les versions précédentes d’Adobe Commerce ne sont pas présents dans la version 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Modules manquants dans Adobe Commerce 2.4.4

Cet article fournit une solution lorsque les modules inclus dans les versions précédentes d’Adobe Commerce ne sont pas présents dans la version 2.4.4.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Vous ne pouvez pas installer de module tiers ou vous êtes rendu compte que certaines des extensions principales regroupées ne sont pas présentes lorsque vous avez effectué la mise à niveau vers Adobe Commerce 2.4.4. Cela ne doit provenir que de l’installation d’un module tiers qui nécessite la suppression de l’une des extensions groupées d’Adobe Commerce 2.4.4 ou si le projet utilise une partie des fonctionnalités de l’un des modules supprimés.

* Scénario 1 : le projet a utilisé l’une des fonctionnalités principales du module regroupé. Le module fourni utilisé n’est pas inclus dans Adobe Commerce 2.4.4. Une fois la mise à niveau vers Adobe Commerce 2.4.4 réussie, vous réalisez que le module et sa fonctionnalité fournie sont manquants.

* Scénario 2 : un module est installé dans votre projet actuel et dépend de l’un des modules regroupés supprimés.

Ce comportement est attendu, car les extensions groupées par fournisseur ont été supprimées de la base de code Adobe Commerce 2.4.4.

## Solution

Installez/achetez les extensions officielles séparément. Elles sont disponibles sur le [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Lecture connexe

[Extensions groupées par fournisseur](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) dans la documentation Adobe Commerce > Informations de mise à jour > Notes de mise à jour d’Adobe Commerce 2.4.4.
