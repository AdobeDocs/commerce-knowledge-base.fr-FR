---
title: L’espace disque MySQL est faible sur Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des solutions pour lorsque vous rencontrez un espace très faible ou aucun espace pour MySQL sur Adobe Commerce sur l’infrastructure cloud. Les symptômes peuvent inclure des pannes de site, des clients incapables d’ajouter des produits au panier, l’impossibilité de se connecter à la base de données, d’accéder à la base de données à distance, et l’impossibilité de SSH dans le noeud. Les symptômes incluent également les erreurs Galera, de synchronisation d’environnement, PHP, de base de données et de déploiement, comme indiqué ci-dessous. Cliquez sur [Solution](https://support.magento.com/hc/en-us/articles/360058472572#solution) pour accéder directement à la section de solution.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# L’espace disque MySQL est faible sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit des solutions pour lorsque vous rencontrez un espace très faible ou aucun espace pour MySQL sur Adobe Commerce sur l’infrastructure cloud. Les symptômes peuvent inclure des pannes de site, des clients incapables d’ajouter des produits au panier, l’impossibilité de se connecter à la base de données, d’accéder à la base de données à distance, et l’impossibilité de SSH dans le noeud. Les symptômes incluent également les erreurs Galera, de synchronisation d’environnement, PHP, de base de données et de déploiement, comme indiqué ci-dessous. Cliquez sur [Solution](https://support.magento.com/hc/en-us/articles/360058472572#solution) pour accéder directement à la section de solution.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problème

La base de données devient trop importante. Les symptômes peuvent inclure la perte de la connexion à la base de données, une erreur de téléchargement de la base de données et divers autres problèmes.

Erreurs que vous pouvez rencontrer :

Galera :

* *SQLSTATE\[08S01\] : Échec du lien de communication : 1047 WSREP n’a pas encore préparé le noeud pour l’utilisation de l’application*   *Erreurs d’importation :*
* *SQLSTATE\[HY000\] : Erreur générale : 1180 Erreur 5 &quot;Erreur d’entrée/de sortie&quot;*
* *SQLSTATE\[08S01\] : Échec du lien de communication : 1047 WSREP n’a pas encore préparé le noeud pour l’utilisation de l’application*

Erreurs de synchronisation d’environnement :

* *SQLSTATE : Erreur générale : 1180 Erreur 5 &quot;Erreur d&#39;entrée/de sortie&quot; lors de la COMMIT*

erreurs PHP :

* *php : PDO ::\_\_build(): le serveur MySQL a disparu.*
* *php errors: PDO::\_\_build(): Error while read greeting packet. PID=NNN.*
* *ERREUR 2013 (HY000) : Perte de la connexion au serveur MySQL lors de la &quot;lecture du paquet de communication initial&quot;, erreur système : 0 &quot;Erreur interne/vérification (pas d&#39;erreur système)&quot;.*

Erreurs de base de données :

* *Error\_code: 1114*
* *InnoDB : erreur (espace disque insuffisant) lors de l&#39;écriture du noeud de mot dans la table d&#39;index auxiliaire FTS.*
* *SQLSTATE\[HY000\] : Erreur générale : le serveur MySQL 2006 a disparu*
* *\[ERROR\] SQL esclave : erreur &#39;Table&#39; `<table\_name>` est plein lors de la requête.*
* *L’unité mysql.service est entrée en échec.*
* *erreur : &quot;Impossible de se connecter au serveur MySQL local via le socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Connexion refusée&quot;)&#39;*
* *1205 Dépassement du délai d’attente du verrouillage ; tentative de redémarrage de la transaction, la requête était : INSERTION DANS \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALEURS (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Erreurs de déploiement :

* *E : Commande &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; état de sortie non nul renvoyé 255*
* *E : Commande &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 restart site-`<environment name>`g-nginx&#39;\]&#39; renvoyé non nul*
* *Mise à niveau du schéma. SQLSTATE\[HY000\] : Erreur générale : 1114 Le tableau `<table\_name>` est plein*
* *SQLSTATE\[HY000\] : Erreur générale : 3 Erreur lors de l’écriture du fichier ./`<environment name>`/\#*
* *W : `<filename>` (Code d’erreur : 28 &quot;Aucun espace laissé sur l’appareil&quot;)*  *Erreurs d’indexation (avec fichiers .ibd temporaires orphelins dans /tmp) :*
* *L’indexeur de règles de catalogue renvoie une exception. Les tables temporaires ne sont pas nettoyées par la suite, puis remplissent le disque sur le noeud maître MySQL actif.*

<u>Étapes à reproduire</u>:

L’une des façons de vérifier si la variable `/data/mysql` (ou partout où le stockage de données MySQL est configuré) est complet en exécutant la commande suivante dans l’interface de ligne de commande :

```bash
df -h
```

Moins de 10 % de la mémoire libre sur le disque MySQL est un indicateur principal d’une panne.

## Cause

La variable `/data/mysql` Le montage peut devenir plein en raison de divers problèmes, tels que le fait de ne pas disposer de suffisamment d’inodes, d’espace de stockage disponible et de requêtes erronées qui génèrent des tables temporaires.

## Solution

Il y a une étape immédiate que vous pouvez prendre pour remettre MySQL sur le piste (ou l’empêcher de se bloquer) : libérer de l’espace en vidant les grandes tables.

Mais une solution à long terme serait d&#39;allouer plus d&#39;espace et de suivre [Bonnes pratiques relatives aux bases de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), y compris l’activation de la variable [Archive de commande/facture/d’envoi](https://docs.magento.com/user-guide/sales/order-archive.html) .

Vous trouverez ci-dessous des informations détaillées sur les solutions rapides et à long terme.

### Vérifier et libérer des informations

Assurez-vous que suffisamment d’informations sont disponibles. Pour cela, exécutez la commande suivante :

```bash
df -i
```

La sortie ressemblerait à ce qui suit :

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Vérifiez que % d’utilisation est inférieur à 70 %. Les noeuds sont corrélés avec des fichiers. Si vous supprimez des fichiers de la partition, vous libérez des informations.

### Vérifier et libérer l’espace de stockage

Vérifiez l’espace de stockage disponible. Pour cela, exécutez :

```bash
df -k
```

La sortie serait similaire à ce qui suit :

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Si le % d’utilisation est supérieur à 70 %, vous devez agir pour libérer/ajouter de l’espace.

### Vérifier les éléments volumineux `ibtmp1` files

Vérifier les éléments volumineux `ibtmp1` fichier sur `/data/mysql` de chaque noeud : ce fichier est le tablespace des tables temporaires. Si des requêtes incorrectes génèrent des tables temporaires, elles sont contenues dans la variable `ibtmp1` fichier . Ce fichier n’est supprimé que lors du redémarrage de la base de données. S&#39;il occupe tout l&#39;espace disponible, la base de données doit être redémarrée. S’il existe de mauvaises requêtes, elles sont recréées à nouveau.

### Vider les grandes tables

>[!WARNING]
>
>Il est vivement recommandé de créer une sauvegarde de la base de données avant toute manipulation et de les éviter pendant les périodes de chargement importantes du site. Voir [Nettoyage de la base](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) dans notre documentation destinée aux développeurs.

Vérifiez s’il existe des tables volumineuses et déterminez si l’une d’elles peut être vidée. Effectuez cette opération sur le noeud principal (source).

Par exemple, les tableaux comportant des rapports peuvent généralement être vidés. Pour plus d’informations sur la recherche de tables volumineuses, voir [Recherche de tables MySQL volumineuses](/help/how-to/general/find-large-mysql-tables.md) article.

S’il n’y a pas d’énormes tableaux de rapport, pensez à vider `_index` pour rétablir l’application Adobe Commerce sur le suivi. `index_price` les tableaux seraient les meilleurs candidats. Par exemple : `catalog_category_product_index_storeX` où X peut avoir des valeurs comprises entre &quot;1&quot; et le nombre maximal de magasins. Veuillez noter que vous devez réindexer pour restaurer les données dans ces tables. Dans le cas de catalogues volumineux, cette réindexation peut prendre beaucoup de temps.

Une fois que vous les videz, attendez que la synchronisation wsrep soit terminée. Vous pouvez désormais créer des sauvegardes et prendre des mesures plus significatives pour ajouter plus d’espace, par exemple allouer/acheter plus d’espace et activer . [Archive de commande/facture/d’envoi](https://docs.magento.com/user-guide/sales/order-archive.html) .

### Vérification des paramètres de journalisation binaire

Vérifiez les paramètres de journalisation binaire de votre serveur MySQL : `log_bin` et `log_bin_index`. Si les paramètres sont activés, les fichiers journaux peuvent devenir énormes. [Création d’un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demande de purge des fichiers journaux binaires volumineux. En outre, demandez à vérifier que la journalisation binaire est correctement configurée afin que les journaux soient purgés régulièrement et ne prennent pas trop d’espace.

Si vous n’avez pas accès aux paramètres du serveur MySQL, demandez à l’assistance technique de le vérifier.

### Allouer/acheter plus d’espace

Allouez plus d’espace disque pour MySQL si vous n’en avez pas. Voir [Vérifier la limite d&#39;espace disque](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) article pour savoir comment vérifier si vous disposez d’espace disque disponible.

* Pour le plan de démarrage, tous les environnements et les environnements d’intégration Pro, vous pouvez allouer l’espace disque si vous n’en utilisez pas. Pour plus d’informations, voir [Allouer plus d’espace pour MySQL](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Pour les environnements d’évaluation et de production professionnels, [support technique](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour allouer plus d’espace disque si vous n’en avez pas utilisé.

Si vous avez atteint votre limite d’espace et que vous rencontrez toujours des problèmes d’espace, envisagez d’acheter plus d’espace disque, contactez votre équipe de compte d’Adobe pour plus de détails.
