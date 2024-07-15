---
title: Restauration d’un instantané de la base de données à partir de l’évaluation ou de la production
description: Cet article explique comment restaurer un instantané de la base de données à partir de l’évaluation ou de la production sur Adobe Commerce sur l’infrastructure cloud.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b99d78845128ca3d995cbbb5df0799449ca954e3
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Restaurer un instantané de la base de données depuis [!DNL Staging] ou [!DNL Production]

Cet article explique comment restaurer une base de données [!DNL snapshot] à partir de [!DNL Staging] ou [!DNL Production] sur l’infrastructure Adobe Commerce on Cloud Pro.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Choisissez la méthode la plus adaptée à votre cas :

* [Méthode 1 : transférez la base de données [!DNL dump] sur votre ordinateur local et importez-la](#meth2).
* [Méthode 2 : importez la base de données  [!DNL dump] directement depuis le serveur](#meth3).

## Méthode 1 : transférer la base de données [!DNL dump] sur votre ordinateur local et l’importer {#meth2}

Les étapes sont les suivantes :

1. En utilisant [!DNL SFTP], accédez à l’emplacement où la base de données [!DNL snapshot] a été placée, généralement sur le premier serveur/noeud de votre [!DNL cluster] (par exemple : `/mnt/recovery-<recovery_id>`). REMARQUE : Si votre projet est basé sur Azure, c’est-à-dire que l’URL de votre projet ressemble à https://us-a1.magento.cloud/projects/&lt;cluster_id>, l’instantané sera placé dans `/mnt/shared/<cluster ID>/all-databases.sql.gz` ou `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` à la place.

   REMARQUE : Le format de l’instantané sur les projets Azure sera différent et contient d’autres bases de données qui ne peuvent pas être importées. Avant d’importer l’instantané, vous devez :     Vous devez prendre des mesures supplémentaires pour extraire la base de données appropriée avant d’importer la sauvegarde.

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
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copiez la base de données [!DNL dump file] (par exemple : `<cluster ID>.sql.gz` pour [!DNL Production] ou `<cluster ID_stg>.sql.gz` pour [!DNL Staging]) sur votre ordinateur local.
1. Assurez-vous d’avoir configuré le [!DNL SSH tunnel] pour vous connecter à la base de données à distance : [[!DNL SSH]  et  [!DNL sFTP] : [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) dans la documentation destinée aux développeurs.
1. Connexion à la base de données.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] de la base de données ; à l’invite [!DNL MariaDB], saisissez :

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

## Méthode 2 : importez la base de données [!DNL dump] directement à partir du serveur {#meth3}

Les étapes sont les suivantes :

1. Accédez à l’emplacement où la base de données [!DNL snapshot] a été placée, généralement sur le premier serveur/noeud de votre [!DNL cluster] (par exemple : `/mnt/recovery-<recovery_id>`).
1. Pour [!DNL drop] et recréer la base de données cloud, connectez-vous d’abord à la base de données :

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] de la base de données ; à l’invite [!DNL MariaDB], saisissez :

   (Pour [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Pour [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Saisissez la commande suivante pour importer le [!DNL snapshot] :

   (Pour importer la sauvegarde de la base de données à partir de [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Pour importer la sauvegarde de la base de données à partir de [!DNL Staging])

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

* [Importer le code : importez la base de données](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots]  et  [!DNL backup] management : [!DNL Dump] votre base de données](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
