---
title: Problèmes après la désactivation d’un module
description: Cet article fournit une solution aux problèmes de fonctionnalité de module après avoir désactivé la sortie de module dans l’administrateur Commerce.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Ayant désactivé la sortie du module dans l’administrateur Commerce, sous **Magasins** > **Paramètres** > **Configuration** > AVANCÉ > **Avancé**, vous pouvez commencer à voir des problèmes liés à la fonctionnalité du module.

## Cause

La désactivation d’une sortie de module sous **Magasins** > **Paramètres** > **Configuration** > AVANCÉ > **Avancé** désactive uniquement la sortie (HTML, JS), mais ne désactive pas la fonctionnalité de ce module.

## Solution

Si vous devez désactiver la fonctionnalité du module, désactivez le module comme décrit dans la section [Activer ou désactiver les modules](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/manage-modules) de notre documentation destinée aux développeurs.

La fonctionnalité de désactivation de la sortie du module a été supprimée à partir de la version 2.2.0.
