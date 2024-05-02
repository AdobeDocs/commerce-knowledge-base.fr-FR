---
title: Le stockage des fichiers est faible, les chargements de pages spécifiques sont lents
description: Cet article fournit une solution au problème d’espace disque faible dû aux images riches et volumineuses.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Le stockage des fichiers est faible, les chargements de pages spécifiques sont lents

Cet article fournit une solution au problème d’espace disque faible dû aux images riches et volumineuses.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions prises en charge
* Adobe Commerce sur site, toutes les versions prises en charge
* Magento Open Source, toutes les versions prises en charge

## Problème

Le faible volume de stockage sur disque et le chargement lent des pages peuvent être causés par de grandes images enrichies utilisant une grande quantité de stockage dans `pub/media/catalog/products` et le partage de l’espace disque entre l’évaluation et la production (sauf si un environnement d’évaluation dédié est configuré).

## Cause

Les images ne sont pas optimisées pour équilibrer les performances et la qualité de l’affichage.

## Solution

Avant de télécharger des images, optimisez-les et compressez-les pour équilibrer les performances avec la qualité d’affichage. Cela permet d’augmenter l’espace et de réduire les temps de chargement des pages. Les fichiers PNG offrent des tailles plus petites pour les images avec de grandes zones de couleur unie. Les JPEG donnent des tailles plus petites pour tout le reste. Utilisez la compression la plus élevée (sans dégradation notable). C&#39;est généralement entre 60 et 80%.

Utilisation [Optimisation rapide des images](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html) pour produire des images plus économes en stockage.

## Lecture connexe

Pour en savoir plus sur la gestion de l’espace disque (si vous utilisez Adobe Commerce sur l’infrastructure cloud), voir [Gestion de l’espace disque dans Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) dans le guide Commerce on Cloud Infrastructure.
