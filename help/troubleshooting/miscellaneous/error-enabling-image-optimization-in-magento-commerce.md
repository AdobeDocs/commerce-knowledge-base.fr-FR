---
title: Erreur lors de l’activation de l’optimisation des images dans Adobe Commerce
description: Cet article fournit une solution au problème de désactivation par défaut de l’optimisation d’images Fastly avec une notification pour contacter Fastly afin d’activer l’optimisation des images. (Fastly Cloud Image Optimizer est un service d’optimisation et de manipulation d’images en temps réel qui accélère la diffusion d’images en diffusant des images à bande passante efficace.)
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Erreur lors de l’activation de l’optimisation des images dans Adobe Commerce

Cet article fournit une solution au problème de désactivation par défaut de l’optimisation d’images Fastly avec une notification pour contacter Fastly afin d’activer l’optimisation des images. (Fastly Cloud Image Optimizer est un service d’optimisation et de manipulation d’images en temps réel qui accélère la diffusion d’images en diffusant des images à bande passante efficace.)

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

Sur la page Configuration rapide, en regard du fragment de code d’E/S Fastly, l’état actuel s’affiche : \_disabled \_avec le message suivant en dessous : Veuillez contacter votre représentant commercial ou envoyer un email à `support@fastly.com` pour demander l’activation de l’optimisation des images pour votre service Fastly.

## Cause

Le site n’est peut-être pas encore en ligne. Des processus sont en place pour précharger le site lorsqu’il sera mis en ligne dans la base de données Fastly.

## Solution

Créez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et demandez l’optimisation de l’image.
