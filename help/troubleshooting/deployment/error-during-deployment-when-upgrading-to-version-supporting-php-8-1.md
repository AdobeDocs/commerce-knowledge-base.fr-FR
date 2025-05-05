---
title: Erreur lors du déploiement lors de la mise à niveau vers une version prenant en charge PHP 8.1
description: Cet article fournit une solution à l’erreur qui se produit lors du déploiement lors de la mise à niveau vers une version prenant en charge PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Erreur lors du déploiement lors de la mise à niveau vers une version prenant en charge PHP 8.1

Cet article fournit une solution à l’erreur qui se produit lors du déploiement lors de la mise à niveau vers une version prenant en charge PHP 8.1.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.4 et versions ultérieures

* Extension ou technologie (Fastly, New Relic, etc.) version PHP 8.1

## Problème

L’erreur suivante se produit lors du déploiement lors de la mise à niveau vers une version prenant en charge PHP 8.1.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Cause

PHP 8.1 inclut déjà la prise en charge de JSON et ne nécessite pas l’installation de l’extension séparément.

## Solution

Supprimez JSON de la section **Runtime** > **Extensions** dans `.magento.app.yaml` et redéployez-la.

## Lecture connexe

[Application PHP](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/app/php-settings) dans notre documentation destinée aux développeurs.
