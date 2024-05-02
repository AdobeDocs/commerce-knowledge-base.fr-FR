---
title: Restauration d’un instantané de la base de données à partir de l’évaluation ou de la production
description: Cet article explique comment restaurer un instantané de la base de données à partir de l’évaluation ou de la production sur Adobe Commerce sur l’infrastructure cloud.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Restauration d’un instantané de la base de données [!DNL Staging] ou [!DNL Production]

Cet article explique comment restaurer une base de données [!DNL snapshot] de [!DNL Staging] ou [!DNL Production] sur l’infrastructure Adobe Commerce on Cloud Pro.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Choisissez la méthode la plus adaptée à votre cas :

* [Méthode 1 : transfert de la base [!DNL dump] sur votre ordinateur local et importez-le](#meth2).
* [Méthode 2 : import de la base de données [!DNL dump] directement à partir du serveur](#meth3).

## Méthode 1 : transfert de la base [!DNL dump] sur votre ordinateur local et importez-le {#meth2}

Les étapes sont les suivantes :

1. Utilisation [!DNL sFTP], accédez à l’emplacement de la base de données. [!DNL snapshot] a été placé, généralement sur le premier serveur/noeud de votre [!DNL cluster] (Par exemple : `/mnt/recovery-<recovery_id>`). REMARQUE : Si votre projet est basé sur Azure, c’est-à-dire si l’URL de votre projet ressemble à https://us-a1.magento.cloud/projects/&lt;cluster_id>, l’instantané est alors placé dans `/mnt/shared/<cluster ID>/all-databases.sql.gz` ou `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` au lieu de .

   REMARQUE : Le format de l’instantané sur les projets Azure sera différent et contient d’autres bases de données qui ne peuvent pas être importées. Avant d&#39;importer l&#39;instantané, vous devez prendre des mesures supplémentaires pour extraire la base de données appropriée avant d&#39;importer la vidage.

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

1. Copier la base de données [!DNL dump file] (Par exemple : `<cluster ID>.sql.gz` pour [!DNL Production] ou `<cluster ID_stg>.sql.gz` pour [!DNL Staging]) sur votre ordinateur local.
1. Assurez-vous que vous avez configuré la variable [!DNL SSH tunnel] pour vous connecter à la base de données à distance : [[!DNL SSH] et [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) dans notre documentation destinée aux développeurs.
1. Connexion à la base de données.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de données ; au niveau de la [!DNL MariaDB] invite, saisissez :

   (Pour [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Pour [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Saisissez la commande suivante pour importer le [!DNL snapshot]:

   (Pour [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Pour [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Méthode 2 : import de la base de données [!DNL dump] directement à partir du serveur {#meth3}

Les étapes sont les suivantes :

1. Accédez à l’emplacement de la base de données. [!DNL snapshot] a été placé, généralement sur le premier serveur/noeud de votre [!DNL cluster] (Par exemple : `/mnt/recovery-<recovery_id>`).
1. À [!DNL drop] et recréez la base de données cloud, connectez-vous d’abord à la base de données :

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de données ; au niveau de la [!DNL MariaDB] invite, saisissez :

   (Pour [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Pour [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Saisissez la commande suivante pour importer le [!DNL snapshot]:

   (Pour [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Pour [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Code d&#39;import : import de la base](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] et [!DNL backup] management : [!DNL Dump] votre base de données](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
