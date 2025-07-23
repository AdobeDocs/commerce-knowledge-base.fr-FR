---
title: L’espace disque [!DNL MySQL] est faible sur Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des solutions pour les cas où l’espace est très faible ou inexistant sur l [!DNL MySQL] infrastructure cloud d’Adobe Commerce. Les symptômes peuvent inclure des pannes de site, l’incapacité des clients à ajouter des produits au panier, l’impossibilité de se connecter à la base de données, l’accès à la base de données à distance, l’impossibilité d’effectuer un SSH dans le nœud . Les symptômes incluent également Galera, la synchronisation de l’environnement, PHP, la base de données et les erreurs de déploiement, comme indiqué ci-dessous. Cliquez sur [Solution](https://support.magento.com/hc/en-us/articles/360058472572#solution) pour accéder directement à la section de la solution.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 660c463850abc145a22c34174aff45ac5ede6707
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---

# L’espace disque [!DNL MySQL] est faible sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit des solutions pour les cas où l’espace disque est très faible ou inexistant sur l’infrastructure cloud d’Adobe Commerce [!DNL MySQL]. Les symptômes incluent des pannes de site, l’incapacité des clients à ajouter des produits au panier, à se connecter à la base de données, à accéder à la base de données à distance et à intégrer SSH au nœud . Les symptômes incluent également Galera, la synchronisation de l’environnement, PHP, la base de données et les erreurs de déploiement, comme indiqué ci-dessous. Cliquez sur [Solution](https://support.magento.com/hc/en-us/articles/360058472572#solution) pour accéder directement à la section de la solution.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problème

La base de données devient trop volumineuse. Les symptômes peuvent inclure la perte de la connexion à la base de données, une erreur de chargement de la base de données et divers autres problèmes.

Erreurs que vous pouvez rencontrer :

Galera :

* *SQLSTATE\[08S01\] : échec du lien de communication : 1047 WSREP n’a pas encore préparé le nœud pour l’utilisation de l’application*   *Erreurs d’import :*
* *SQLSTATE\[HY000\] : Erreur générale : 1180 Erreur de type 5 « Erreur d&#39;entrée/sortie »*
* *SQLSTATE\[08S01\] : échec du lien de communication : 1047 WSREP n’a pas encore préparé le nœud pour l’utilisation de l’application*

Erreurs de synchronisation de l’environnement :

* *SQLSTATE : Erreur générale : 1180 Erreur de type 5 « Erreur d’entrée/sortie » lors de la validation*

Erreurs PHP :

* *php: PDO::\_\_build() : [!DNL MySQL] serveur est parti.*
* *erreurs php : PDO::\_\_build() : erreur lors de la lecture du paquet de salutation. PID=NNNN.*
* *ERROR 2013 (HY000) : connexion perdue au serveur [!DNL MySQL] lors de la &#39;lecture du paquet de communication initial&#39;, erreur système : 0 « Erreur interne/vérification (pas d&#39;erreur système) ».*

Erreurs de base de données :

* *Error\_code : 1114*
* *InnoDB : erreur (espace disque insuffisant) lors de l’écriture du nœud de mots dans la table d’index auxiliaire FTS.*
* *SQLSTATE\[HY000\] : Erreur générale : le serveur [!DNL MySQL] 2006 est parti*
* *\[ERROR\] SQL esclave : erreur &#39;La table `<table\_name>` est pleine&#39; sur la requête.*
* *L’unité mysql.service est entrée dans un état d’échec.*
* *erreur : &#39;Impossible de se connecter au serveur [!DNL MySQL] local via le socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 « Connexion refusée »)&#39;*
* *1205 Délai d’attente du verrouillage dépassé. Essayez de redémarrer la transaction, la requête était : INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALUES (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Erreurs de déploiement :

* *E : la commande &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; a renvoyé un état de sortie non nul 255*
* *E : la commande &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 restart site-`<environment name>`g-nginx&#39;\]&#39; a renvoyé une valeur non nulle*
* *Mise à niveau du schéma.. SQLSTATE\[HY000\] : Erreur générale : 1114 La table `<table\_name>` est pleine*
* *SQLSTATE\[HY000\] : Erreur générale : 3 Erreur lors de l’écriture du fichier ./`<environment name>`/\#*
* *W : `<filename>` (code d’erreur : 28 « Aucun espace restant sur l’appareil »)* *Erreurs d’indexation (avec les fichiers .ibd temporaires orphelins dans /tmp) :*
* *L’indexeur de règles de catalogue renvoie une exception. Les tables temporaires ne sont pas nettoyées par la suite, puis elles remplissent le disque sur le nœud principal de [!DNL MySQL] actuel*

<u>Procédure à suivre </u> :

L’une des façons de vérifier si le `/data/mysql` (ou l’endroit où [!DNL MySQL] stockage de données est configuré) est plein est d’exécuter la commande suivante dans l’interface de ligne de commande :

```bash
df -h
```

Moins de 10 % de la mémoire libre sur [!DNL MySQL] disque est le principal indicateur d&#39;une panne.

## Cause

Le montage `/data/mysql` peut devenir saturé en raison de divers problèmes, tels que le manque d’inodes, l’espace de stockage disponible et les requêtes erronées qui génèrent des tables temporaires.

## Solution

Il y a une étape immédiate que vous pouvez prendre pour remettre les [!DNL MySQL] sur les rails (ou les empêcher de se coincer) : libérez de l&#39;espace en tirant les grandes tables.

Mais une solution à long terme consisterait à allouer plus d&#39;espace et à suivre les [bonnes pratiques de base de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), y compris en activant la fonctionnalité [Archivage des commandes/factures/expéditions](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

Vous trouverez ci-dessous des informations détaillées sur les solutions rapides et à long terme.

### Vérifier et libérer des nœuds

Assurez-vous qu’il y a suffisamment d’inodes disponibles. Pour cela, exécutez la commande suivante :

```bash
df -i
```

La sortie ressemblerait à ce qui suit :

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Vérifiez que le % d&#39;utilisation est &lt;70%. Les nœuds sont corrélés aux fichiers. Si vous supprimez des fichiers de la partition, vous libérez des inodes.

### Vérifier et libérer de l&#39;espace de stockage

Vérifiez l’espace de stockage disponible. Pour cela, exécutez :

```bash
df -k
```

La sortie serait similaire à ce qui suit :

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Si le % d’utilisation est >70 %, vous devez prendre des mesures pour libérer/ajouter de l’espace.

### Rechercher les fichiers `ibtmp1` volumineux

Recherchez un fichier `ibtmp1` volumineux sur les `/data/mysql` de chaque nœud : ce fichier est l&#39;espace disque logique pour les tables temporaires. Si des requêtes incorrectes génèrent des tables temporaires, elles sont contenues dans le fichier `ibtmp1`. Ce fichier n&#39;est supprimé que lors du redémarrage de la base de données. S&#39;il occupe tout l&#39;espace disponible, la base de données doit être redémarrée. S’il existe des requêtes incorrectes, elles seront recréées.

### Vider les grandes tables

>[!WARNING]
>
>Nous vous recommandons vivement de créer une sauvegarde de base de données avant d’effectuer toute manipulation et de les éviter pendant les périodes de charge élevée du site. Voir [Vidanger votre base de données](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) dans notre documentation destinée aux développeurs.

Vérifiez s&#39;il existe de grandes tables et envisagez si l&#39;une d&#39;entre elles peut être nettoyée. Effectuez cette opération sur le nœud principal (source).

Par exemple, les tableaux contenant des rapports peuvent généralement être vidés. Pour plus d’informations sur la recherche de tables volumineuses, reportez-vous à l’article [Rechercher de grandes [!DNL MySQL] tables](/help/how-to/general/find-large-mysql-tables.md).

S’il n’existe pas de tables de rapports volumineuses, envisagez de vider `_index` tables afin de remettre l’application Adobe Commerce sur la bonne voie. `index_price` tables seraient les meilleures candidates. Par exemple, les tableaux `catalog_category_product_index_storeX`, où X peut avoir des valeurs comprises entre « 1 » et le nombre maximal de magasins. N’oubliez pas que vous devrez effectuer une réindexation pour restaurer les données de ces tables. Dans le cas de catalogues volumineux, cette réindexation peut prendre beaucoup de temps.

Une fois que vous les avez vidés, attendez la fin de la synchronisation de l’étape. Vous pouvez maintenant créer des sauvegardes et prendre des mesures plus importantes pour ajouter de l’espace, comme allouer/acheter plus d’espace et activer la fonctionnalité [Archivage des commandes/factures/envois](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

### Vérifier les paramètres de journalisation binaire

Vérifiez les paramètres de journalisation binaire de votre serveur [!DNL MySQL] : `log_bin` et `log_bin_index`. Si les paramètres sont activés, les fichiers journaux peuvent devenir volumineux. [Créez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant la purge des fichiers journaux binaires volumineux. Demandez également à de vérifier que la journalisation des fichiers binaires est correctement configurée afin que les journaux soient purgés périodiquement et ne prennent pas trop d’espace.

Si vous n’avez pas accès aux paramètres du serveur [!DNL MySQL], demandez de l’aide pour les vérifier.

### Récupérer l’espace disque alloué inutilisé

1. SSH dans le nœud un et connectez-vous à MySQL :

   ```sh
   mysql -h127.0.0.1 -p`php -r "echo (include('app/etc/env.php'))['db']['connection']['default']['password'];"` -u`whoami` `whoami`
   ```

   Pour obtenir des instructions détaillées, reportez-vous à la section [Connexion et exécution de requêtes sur la base de données Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/remote-db-connection-execute-queries).

1. Recherchez l’espace inutilisé :

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) AS size_MB, round((data_free)/1048576,2) AS Allocated_but_unused FROM information_schema.tables WHERE data_free > 1048576*10 ORDER BY data_free DESC;
   ```


   Exemple de sortie :

   | table_name | size_MB | Alsigned_but_unused |
   |----------------------|----------|--------------------------|
   | sales_order_grid | 28145,20 | 14943,00 |


   Vérifiez dans la sortie si de la mémoire a été allouée mais n&#39;est pas utilisée. Cela se produit lorsque des données ont été supprimées d’une table, mais que la mémoire est toujours allouée à cette table.


1. Placez votre site en mode de maintenance et arrêtez les tâches cron afin qu’aucune interaction ne se produise sur la base de données. Pour connaître les étapes, reportez-vous aux sections [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) et [Désactivation des tâches cron](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).
1. Récupérez cet espace en recréant le tableau à l’aide de la commande suivante (par exemple en utilisant le tableau répertorié ci-dessus avec l’espace le plus inutilisé) :

   ```sql
   ALTER TABLE sales_order_grid Engine = "INNODB";
   ```

1. Exécutez la requête suivante pour vérifier l’espace non alloué pour chaque table qui affiche une valeur élevée dans la **[!UICONTROL Allocated_but_unused]** de colonne.

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) as size_MB, round((data_free)/1048576,2) as Allocated_but_unused FROM information_schema.tables WHERE 1 AND data_free > 1048576*10 ORDER BY 
   data_free DESC;
   ```


1. Maintenant [Désactivez le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#enable-or-disable-maintenance-mode-1) et [Activez les tâches cron](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).


### Allouer/acheter plus d&#39;espace

Allouez plus d’espace disque aux [!DNL MySQL] si vous en avez inutilisé. Consultez l’article [Vérification de la limite d’espace disque](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) pour savoir comment vérifier si vous disposez d’espace disque disponible.

* Pour le plan de démarrage, tous les environnements et les environnements d’intégration de plan Pro, vous pouvez allouer l’espace disque si vous avez des éléments inutilisés. Pour plus d’informations, voir la section [Allouer plus d’espace pour [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Pour les environnements d’évaluation et de production ProPlan, [contactez l’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour allouer plus d’espace disque si vous en avez inutilisé.

Si vous avez atteint votre limite d’espace et rencontrez toujours des problèmes d’espace disque faible, pensez à acheter plus d’espace disque. Pour plus d’informations, contactez l’équipe chargée de votre compte Adobe.

## Lecture connexe

[Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
