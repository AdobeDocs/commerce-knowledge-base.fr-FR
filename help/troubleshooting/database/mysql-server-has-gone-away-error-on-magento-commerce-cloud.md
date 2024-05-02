---
title: Le serveur MySQL a disparu ​ erreur sur Adobe Commerce dans le cloud
description: Cet article traite de la solution au problème où vous recevez un message d’erreur "SQL Server has gone*" (Le serveur SQL a disparu) dans le fichier "cron.log". Plusieurs symptômes, dont des problèmes d’importation de fichiers image ou un échec de déploiement, peuvent être ressentis.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Le serveur MySQL a disparu &#x200B; erreur sur Adobe Commerce dans le cloud

Cet article décrit la solution au problème pour lequel vous recevez une *Le serveur SQL a disparu* &quot; message d’erreur dans la variable `cron.log` fichier . Plusieurs symptômes, dont des problèmes d’importation de fichiers image ou un échec de déploiement, peuvent être ressentis.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

Vous recevez un *Le serveur SQL a disparu* &quot; message d’erreur dans la variable `cron.log` fichier .

<u>Étapes à reproduire</u>

Importez des fichiers et déclenchez un déploiement.

<u>Résultat attendu</u>

Déploiement réussi.

<u>Résultat réel</u>

Message d’erreur dans `cron.log` :&quot; *SQLSTATE\[HY00\] \[2006\] Le serveur MySQL a disparu at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Cause

La variable `default_socket_timeout` est définie sur une valeur trop basse. Cela est dû au paramètre `default_socket_timeout` . Si php ne reçoit rien de la base de données MySQL au cours de cette période, il suppose qu’il est déconnecté et renvoie l’erreur.

## Solution

1. Vérifier le délai d’expiration actuel pour `default_socket_timeout` en exécutant dans l’interface de ligne de commande :    ```    php -i |grep default_socket_timeout    ```
1. Selon l’augmentation du paramètre de délai d’expiration, la variable `default_socket_timeout` à la durée d’exécution la plus longue possible attendue dans la variable `/etc/platform/<project_name>/php.ini` fichier . Il est conseillé de définir entre 10 et 15 minutes.
1. Validez-le dans GIT et redéployez-le.

## Lecture connexe

* [Le chargement de la base de données perd la connexion à MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
