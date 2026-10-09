---
title: MySQL server a disparu​ erreur sur Adobe Commerce on cloud
description: Cet article présente la solution au problème de réception d’un message d’erreur « *SQL Server has go away* » dans le fichier « cron.log ». Différents symptômes peuvent se manifester, notamment des problèmes d’importation de fichiers image ou un échec de déploiement.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%
---
# MySQL server a disparu&#x200B; erreur sur Adobe Commerce on cloud

Cet article aborde la solution au problème de réception d’un message d’erreur « *Le serveur SQL est parti* » dans le fichier `cron.log`. Différents symptômes peuvent se manifester, notamment des problèmes d’importation de fichiers image ou un échec de déploiement.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

Vous recevez un message d’erreur « *le serveur SQL est parti* » dans le fichier `cron.log`.

<u>Procédure à suivre</u>

Importez des fichiers et déclenchez un déploiement.

<u>Résultat attendu</u>

Déploiement réussi.

<u>Résultat réel</u>

Message d’erreur dans `cron.log` : » *SQLSTATE\[HY000\] \[2006\] MySQL Server a disparu at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144 »*

## Cause

La valeur `default_socket_timeout` est trop basse. Cela est dû au paramètre `default_socket_timeout` . Si php ne reçoit rien de la base de données MySQL pendant cette période, il suppose qu&#39;il est déconnecté et renvoie l&#39;erreur.

## Solution

1. Vérifiez le délai d’expiration actuel pour `default_socket_timeout` en exécutant dans l’interface de ligne de commande : `php -i |grep default_socket_timeout`.
1. Vérifiez le délai d’expiration actuel pour `default_socket_timeout` en exécutant dans l’interface de ligne de commande : `php -i |grep default_socket_timeout`
1. En fonction de l’augmentation du paramètre de délai d’expiration, la variable `default_socket_timeout` prend la durée d’exécution la plus longue possible attendue dans le fichier `/etc/platform/<project_name>/php.ini`. Il est suggéré de définir entre 10 et 15 minutes.
1. Validez-le dans Git et redéployez-le.

## Lecture connexe

* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
