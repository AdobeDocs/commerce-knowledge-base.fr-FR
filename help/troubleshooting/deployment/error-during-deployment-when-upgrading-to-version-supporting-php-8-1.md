---
title: Erreur lors du déploiement lors de la mise à niveau vers la version prenant en charge PHP 8.1
description: Cet article fournit une solution pour l'erreur qui se produit lors du déploiement lors de la mise à niveau vers une version qui prend en charge PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%
---
# Erreur lors du déploiement lors de la mise à niveau vers la version prenant en charge PHP 8.1

Cet article fournit une solution pour l&#39;erreur qui se produit lors du déploiement lors de la mise à niveau vers une version qui prend en charge PHP 8.1.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.4.4. et plus tard

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

PHP 8.1 inclut déjà la prise en charge de JSON et ne nécessite pas que l&#39;extension soit installée séparément.

## Solution

Supprimez JSON de la section **Runtime** > **Extensions** dans `.magento.app.yaml` et redéployez.

## Lecture connexe

[Application PHP](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings) dans notre documentation destinée aux développeurs.
