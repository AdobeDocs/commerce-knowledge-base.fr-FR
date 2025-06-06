---
title: Restaurer un instantané de base de données à partir de l’évaluation ou de la production
description: Cet article explique comment restaurer un instantané de base de données à partir de l’évaluation ou de la production sur Adobe Commerce sur une infrastructure cloud.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 3d75b53dd290731380b2da33e3c0a1f746b9275b
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Restaurer un instantané de base de données à partir de [!DNL Staging] ou [!DNL Production]

Cet article explique comment restaurer une base de données [!DNL snapshot] à partir de [!DNL Staging] ou [!DNL Production] sur l’infrastructure Adobe Commerce sur Cloud Pro.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Choisissez la solution la plus adaptée à votre cas :

* [Méthode 1 : transférer la base de données  [!DNL dump]  votre ordinateur local et l’importer](#meth2).
* [Méthode 2 : importer la base  [!DNL dump]  données directement depuis le serveur](#meth3).

## Méthode 1 : transférer le [!DNL dump] de la base de données vers votre ordinateur local et l&#39;importer {#meth2}

Les étapes sont les suivantes :

1. À l’aide de [!DNL SFTP], accédez à l’emplacement où le [!DNL snapshot] de base de données a été placé, généralement sur le premier serveur/nœud de votre [!DNL cluster] (par exemple : `/mnt/recovery-<recovery_id>`). REMARQUE : si votre projet est basé sur Azure, c’est-à-dire que l’URL de votre projet ressemble à https://us-a1.magento.cloud/projects/&lt;cluster_id>, l’instantané est placé dans `/mnt/shared/<cluster ID>/all-databases.sql.gz` ou `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` à la place.

   REMARQUE : le format de l&#39;instantané sur les projets Azure sera différent et contient d&#39;autres bases de données qui ne peuvent pas être importées. Avant d’importer l’instantané, vous devez :     doivent prendre des mesures supplémentaires pour extraire la base de données appropriée avant d’importer l’image mémoire.

   Pour la production :

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   Pour l’évaluation :

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: <cluster ID_stg>/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copiez le [!DNL dump file] de la base de données (par exemple : `<cluster ID>.sql.gz` pour [!DNL Production] ou `<cluster ID_stg>.sql.gz` pour [!DNL Staging]) sur votre ordinateur local.
1. Vérifiez que vous avez configuré la [!DNL SSH tunnel] pour vous connecter à la base de données à distance : [[!DNL SSH] et [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn) dans notre documentation destinée aux développeurs.
1. Connexion à la base de données.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de données ; à l’invite de [!DNL MariaDB], saisissez :

   (Pour [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Pour [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Saisissez la commande suivante pour importer le [!DNL snapshot] :

   (Pour [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Pour [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Méthode 2 : importer la base de données [!DNL dump] directement depuis le serveur {#meth3}

Les étapes sont les suivantes :

1. Accédez à l’emplacement où la [!DNL snapshot] de base de données a été placée, généralement sur le premier serveur/nœud de votre [!DNL cluster] (par exemple : `/mnt/recovery-<recovery_id>`).
1. Pour [!DNL drop] et recréer la base de données cloud, connectez-vous d’abord à la base de données :

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de données ; à l’invite de [!DNL MariaDB], saisissez :

   (Pour [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Pour [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Après avoir déposé la base de données, recréez la base de données :

   ```mysql
   create database [database_name];
   ```

1. Saisissez la commande suivante pour importer le [!DNL snapshot] :

   (Pour importer la sauvegarde de la base de données depuis [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Pour importer la sauvegarde de la base de données depuis [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Pour importer une sauvegarde de base de données à partir de tout autre environnement)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Pour importer une sauvegarde de base de données à partir de tout autre environnement)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Code d’import : import de la base de données](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] and [!DNL backup] management :  [!DNL Dump]  votre base de données](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Sauvegarde (instantané) sur le cloud : FAQ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
