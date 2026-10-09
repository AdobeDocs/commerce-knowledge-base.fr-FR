---
title: Erreur de niveau d’imbrication de la fonction maximale xdebug d’installation
description: Cet article fournit un correctif pour l’erreur de niveau d’imbrication de la fonction maximale xdebug lors de l’installation.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# Erreur de niveau d’imbrication de la fonction maximale xdebug d’installation

Cet article fournit un correctif pour l’erreur de niveau d’imbrication de la fonction maximale xdebug lors de l’installation.

## Détails

Lors de l’installation d’Adobe Commerce, un message similaire au suivant s’affiche :

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Il est vivement recommandé de NE PAS UTILISER `xdebug` dans un environnement de production.

## Solution

Il existe un problème connu avec `xdebug` qui peut affecter les installations d’Adobe Commerce ou l’accès au storefront ou à Commerce Admin après l’installation.

Pour plus d’informations, consultez [Problème connu avec xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) dans notre base de connaissances d’assistance.
