---
title: Problèmes après la désactivation d’un module
description: Cet article fournit une solution aux problèmes de fonctionnalité de module après avoir désactivé la sortie de module dans l’administrateur Commerce.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Problèmes après la désactivation d’un module

Cet article fournit une solution aux problèmes de fonctionnalité de module après avoir désactivé la sortie de module dans l’administrateur Commerce.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.1.X ou version antérieure
* Adobe Commerce On-Premise 2.1.X ou version antérieure

## Problème

Désactivation de la sortie du module dans l’administrateur Commerce, sous **Magasins** > **Paramètres** > **Configuration** > AVANCÉ > **Avancé**, vous pouvez commencer à voir les problèmes liés à la fonctionnalité du module.

## Cause

Désactivation d’une sortie de module sous **Magasins** > **Paramètres** > **Configuration** > AVANCÉ > **Avancé** désactive uniquement la sortie (HTML, JS), mais ne désactive pas la fonctionnalité de ce module.

## Solution

Si vous devez désactiver la fonctionnalité du module, désactivez le module comme décrit dans la section [Activation ou désactivation des modules](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html) dans notre documentation destinée aux développeurs.

La fonctionnalité de désactivation de la sortie du module a été supprimée à partir de la version 2.2.0.
