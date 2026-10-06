---
title: Vérification des requêtes lentes et des processus MySQL
description: Cet article aborde quelques problèmes courants de MySQL (requêtes lentes, processus prenant trop de temps) qui peuvent avoir un impact négatif sur le site d’un commerçant et sur les solutions qu’ils indiquent.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%
---
# Vérification des requêtes lentes et des processus MySQL

Cet article aborde quelques problèmes courants de MySQL (requêtes lentes, processus prenant trop de temps) qui peuvent avoir un impact négatif sur le site d’un commerçant et sur les solutions qu’ils indiquent.

## Vérification des « requêtes lentes » MySQL

### Description

Si vous avez rencontré une panne potentiellement due à une surcharge de la base de données, ces étapes vous aideront à vérifier le journal des requêtes lentes de votre base de données.

### Analyser les requêtes à l’aide de la ligne de commande MySQL (Adobe Commerce Cloud/on-premise/Magento Open Source)

1. Connectez-vous à votre ligne de commande MySQL (Adobe Commerce on-premise/Magento Open Source) ou à votre serveur cloud à partir de la ligne de commande (Adobe Commerce sur l’infrastructure cloud).
1. Examinez le journal des requêtes lentes pour les requêtes de plus de 50 secondes :

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Accédez à <https://www.unixtimestamp.com/> (ou à un convertisseur d’horodatage Unix similaire) et insérez l’horodatage du moment où la requête lente a été exécutée.
1. Si l’heure correspond à une panne du site que vous avez rencontrée, elle peut être due à une surcharge de la base de données. Vérifiez quels chargements se trouvaient dans la base de données à ce moment-là. Ces charges peuvent être par exemple :

* Processus cron
* Trafic (robots ou personnes)
* Scripts d’import/export
* Création d’images mémoire


### Analysez les requêtes à l’aide de l’[!DNL Percona Toolkit] (Adobe Commerce Pro : architecture cloud uniquement).

Si votre projet Adobe Commerce est déployé sur une architecture Pro, vous pouvez utiliser le [!DNL Percona Toolkit] pour analyser les requêtes.

1. Exécutez la commande `pt-query-digest --type=slowlog` sur les journaux de requêtes lentes MySQL.
   * Pour trouver l’emplacement des journaux de requêtes lentes, consultez **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)** dans notre documentation destinée aux développeurs.
   * Voir la documentation [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) .
1. En fonction des problèmes trouvés, prenez les mesures nécessaires pour corriger la requête, afin qu’elle s’exécute plus rapidement.

## Vérification de la « liste de processus » MySQL

### Description

Cela permet de déterminer si le serveur MySQL est actif et s’il n’existe aucune requête bloquée.

### Étapes

1. Connectez-vous à votre ligne de commande MySQL (Adobe Commerce on-premise/Magento Open Source) ou à votre serveur cloud à partir de la ligne de commande (Adobe Commerce sur l’infrastructure cloud).
1. Connectez-vous à MySQL en utilisant le bloc de code ci-dessous. Cela automatisera le processus de connexion.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Si vous obtenez une erreur en retour ou si la réponse dure plus de 30 secondes, vous devez contacter le support technique pour vérifier le serveur MySQL.
1. Examiner l’exemple de sortie.

1. Voici un exemple de sortie :

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Vérifiez la colonne « Durée » pour toute durée supérieure à 1 800 secondes ; cela indique un processus dont l’exécution peut prendre trop de temps. Notez l’état des processus dans la colonne « État ».
1. Passez en revue les requêtes et, éventuellement, supprimez-les si vous estimez qu’elles ne doivent pas s’exécuter pendant cette durée. Il est possible que les requêtes à exécution longue soient attendues.


## Lecture connexe

* [MySQL Afficher la syntaxe Processlist](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) dans dev.mysql.com.
* [Syntaxe MySQL Kill](https://dev.mysql.com/doc/refman/8.0/en/kill.html) dans dev.mysql.com.
* [Sécurité, performances et gestion des données](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) dans notre documentation destinée aux développeurs.
* [Aide MySQL](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) dans notre documentation destinée aux développeurs.
