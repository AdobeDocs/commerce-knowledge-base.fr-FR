---
title: MySQL server a disparu​ erreur sur Adobe Commerce on cloud
description: Cet article présente la solution au problème de réception d’un message d’erreur « *SQL Server has go away* » dans le fichier « cron.log ». Différents symptômes peuvent se manifester, notamment des problèmes d’importation de fichiers image ou un échec de déploiement.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '267'
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

1. Vérifiez le délai d’expiration actuel pour `default_socket_timeout` en exécutant dans l’interface de ligne de commande :    ```    php -i |grep default_socket_timeout    ```
1. En fonction de l’augmentation du paramètre de délai d’expiration, la variable `default_socket_timeout` prend la durée d’exécution la plus longue possible attendue dans le fichier `/etc/platform/<project_name>/php.ini`. Il est suggéré de définir entre 10 et 15 minutes.
1. Validez-le dans Git et redéployez-le.

## Lecture connexe

* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
