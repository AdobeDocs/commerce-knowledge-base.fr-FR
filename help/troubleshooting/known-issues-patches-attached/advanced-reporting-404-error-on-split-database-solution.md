---
title: Erreur de création de rapports avancée 404 sur la solution de base de données partagée
description: Cet article fournit un correctif pour les utilisateurs d’Adobe Commerce 2.3.x avec la [solution de base de données partagée](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) qui rencontre une erreur 404 lors de la tentative d’utilisation du reporting avancé.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Erreur de création de rapports avancée 404 sur la solution de base de données partagée

Cet article fournit un correctif aux utilisateurs d’Adobe Commerce 2.3.x avec la variable [solution de base de données partagée](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) qui génère une erreur 404 lors de la tentative d’utilisation du reporting avancé.

## Produits et versions concernés

Adobe Commerce 2.3.0 - 2.3.5-p1

## Problème

Le correctif corrige le problème en raison duquel un nom de connexion incorrect est utilisé pour collecter les données de guillemets. En raison du nom de connexion incorrect utilisé, les données de guillemet ne sont pas envoyées à Magento Business Intelligence (MBI) et les rapports ne peuvent pas être générés.

## Solution

Appliquez la variable [correctif](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, cliquez sur le lien suivant :

[MDVA-26831\_EE\_2.3.4\_v1.compositeur.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Comment appliquer le correctif

Décompressez le fichier et suivez les instructions de la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
