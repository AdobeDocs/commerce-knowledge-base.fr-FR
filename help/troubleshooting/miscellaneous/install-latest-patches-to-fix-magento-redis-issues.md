---
title: Installez les derniers correctifs pour résoudre les problèmes liés aux redis d’Adobe Commerce
description: Cet article fournit des informations sur les derniers correctifs liés aux Redis disponibles dans le package [Adobe Commerce on cloud infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html).
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installez les derniers correctifs pour résoudre les problèmes liés aux redis d’Adobe Commerce

Cet article fournit des informations sur les derniers correctifs liés aux Redis disponibles dans [Correctifs d’infrastructure cloud d’Adobe Commerce](https://devdocs.magento.com/cloud/project/project-patch.html) module.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.3.3, 2.3.4

## Problème

La consommation supplémentaire de processeur et de mémoire par Redis peut réduire les performances d’Adobe Commerce et donc les performances globales de votre site web.

## Solution

Appliquez les derniers correctifs fournis par Adobe Commerce sur le package Correctifs d’infrastructure cloud. Pour obtenir des instructions détaillées, voir [Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

Les derniers correctifs Redis fournis par Adobe Commerce sur le package Correctifs d’infrastructure cloud contribuent aux éléments suivants :

* réduction de la taille de la communication réseau pour Redis
* correction des conditions de concurrence conduisant à une consommation de mémoire supplémentaire ;
* modification de l’adaptateur cache pour couvrir les cas d’expulsion
* diminution de la consommation du processeur Redis

Adobe Commerce recommande également d’effectuer une mise à niveau vers Redis 5 si vous exécutez Adobe Commerce sur l’infrastructure cloud 2.3.3 ou version ultérieure.
