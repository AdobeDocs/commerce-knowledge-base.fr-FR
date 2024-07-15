---
title: Erreur d’imbrication de la fonction maximale d’installation xdebug
description: Cet article fournit un correctif pour l’erreur de niveau d’imbrication de fonction xdebug maximum pendant l’installation.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Erreur d’imbrication de la fonction maximale d’installation xdebug

Cet article fournit un correctif pour l’erreur de niveau d’imbrication de fonction xdebug maximum pendant l’installation.

## Détails

Lors de l’installation d’Adobe Commerce, un message similaire à celui-ci s’affiche :

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Il est vivement recommandé de NE PAS UTILISER `xdebug` dans un environnement de production.

## Solution

Il existe un problème connu avec `xdebug` qui peut affecter les installations Adobe Commerce ou l’accès au storefront ou à l’administrateur Commerce après l’installation.

Pour plus d’informations, voir [Problème connu avec xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) dans notre base de connaissances de support.
