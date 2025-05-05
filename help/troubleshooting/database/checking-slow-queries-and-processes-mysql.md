---
title: Vérification des requêtes et processus lents MySQL
description: Cet article présente quelques problèmes courants de MySQL (requêtes lentes, processus qui prennent trop de temps) qui peuvent avoir un impact négatif sur le site d’un commerçant et sur les solutions qu’il indique.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Vérification des requêtes et processus lents MySQL

Cet article présente quelques problèmes courants de MySQL (requêtes lentes, processus qui prennent trop de temps) qui peuvent avoir un impact négatif sur le site d’un commerçant et sur les solutions qu’il indique.

## Vérification des &quot;requêtes lentes&quot; MySQL

### Description

Si une panne a pu être provoquée par une base de données surchargée, ces étapes vous aideront à vérifier le journal des requêtes lentes de votre base de données.

### Analyse des requêtes à l’aide de la ligne de commande MySQL (Adobe Commerce Cloud/on-site/Magento Open Source)

1. Connectez-vous à votre ligne de commande MySQL (Adobe Commerce sur site/Magento Open Source) ou à votre serveur cloud à partir de la ligne de commande (Adobe Commerce sur l’infrastructure cloud).
1. Examinez le journal des requêtes lentes pour les requêtes de plus de 50 secondes :

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Accédez à <https://www.unixtimestamp.com/> (ou à un convertisseur d’horodatage Unix similaire) et insérez l’horodatage du moment où la requête lente a été exécutée.
1. Si le temps correspond à une panne de site, elle peut être due à une base de données surchargée. Vérifiez les chargements présents dans la base de données à ce moment-là. Voici quelques exemples de charge :

* Processus cron
* Trafic (robots ou personnes)
* Importation/exportation de scripts
* Création de vidages


### Analysez les requêtes à l’aide de [!DNL Percona Toolkit] (architecture Adobe Commerce Pro : cloud uniquement)

Si votre projet Adobe Commerce est déployé sur l’architecture Pro, vous pouvez utiliser le [!DNL Percona Toolkit] pour analyser les requêtes.

1. Exécutez la commande `pt-query-digest --type=slowlog` sur les journaux de requête lents MySQL.
   * Pour trouver l’emplacement des journaux de requêtes lentes, voir **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=fr)** dans notre documentation destinée aux développeurs.
   * Consultez la documentation [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) .
1. En fonction des problèmes détectés, suivez les étapes pour corriger la requête afin qu’elle s’exécute plus rapidement.

## Vérification de la &quot;liste des processus&quot; MySQL

### Description

Cela permet d’identifier si le serveur MySQL est actif et s’il n’y a aucune requête bloquée.

### Étapes

1. Connectez-vous à votre ligne de commande MySQL (Adobe Commerce sur site/Magento Open Source) ou à votre serveur cloud à partir de la ligne de commande (Adobe Commerce sur l’infrastructure cloud).
1. Connectez-vous à MySQL à l’aide du bloc de code ci-dessous. Cela automatisera le processus de connexion.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Si vous obtenez une erreur ou qu’il faut plus de 30 secondes pour répondre, contactez le support pour vérifier le serveur MySQL.
1. Affichage d’un exemple de sortie.

1. Voici un exemple de sortie :

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Cochez la colonne &quot;Heure&quot; pour toute période supérieure à 1 800 secondes ; cela indique un processus qui prend potentiellement trop de temps pour se terminer. Notez l’état des processus dans la colonne &quot;Etat&quot;.
1. Examinez les requêtes et tuez-les s’il s’avère qu’elles ne s’exécutent pas pendant cette durée. Il est possible que les requêtes longues soient attendues.


## Lecture connexe

* [MySQL Show Processlist Syntax](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) dans dev.mysql.com.
* [Syntaxe de la mort MySQL](https://dev.mysql.com/doc/refman/8.0/en/kill.html) dans dev.mysql.com.
* [Sécurité, performance et gestion des données](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) dans notre documentation destinée aux développeurs.
* [Aide de MySQL](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) dans notre documentation destinée aux développeurs.
