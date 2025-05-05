---
title: Le chargement de la base de données perd la connexion à MySQL
description: Cet article fournit une solution lorsque le téléchargement de la base de données perd la connexion à MySQL.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Le chargement de la base de données perd la connexion à MySQL

Cet article fournit une solution lorsque le téléchargement de la base de données perd la connexion à MySQL.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

La base de données ne se charge pas dans les branches d’intégration/principale sur l’architecture de plan Adobe Commerce sur l’infrastructure cloud Pro, ni dans aucune branche sur l’architecture de plan de démarrage de l’infrastructure cloud d’Adobe Commerce, le symptôme étant l’impossibilité de se connecter. Cette erreur s’affiche dans l’interface de ligne de commande.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Cause

Cela est généralement dû à un manque d’espace disque pour l’importation de la base de données.

## Solution

Vérifiez si l’espace disque manque. Pour ce faire, exécutez la commande `netcat` dans l’interface de ligne de commande par rapport au port de base de données 3306 ; un message complet s’affiche sur le disque s’il est plein :

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

Vous devrez allouer plus d’espace pour la base de données dans votre `services.yaml` et la déployer si vous n’avez pas d’espace disponible. Pour connaître les étapes, voir [Espace disque du service](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space).

Remarque : dans le plan d’architecture Pro, vous pouvez vérifier l’espace alloué sur votre partition en exécutant la commande suivante : `df -h`

Attendez-vous à une sortie similaire à la sortie suivante. Dans cet exemple, 10 Go des 25 Go alloués sont utilisés, 15 Go d’espace MySQL n’étant pas utilisés.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Lecture connexe

[Gérer l’espace disque](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) dans notre documentation destinée aux développeurs
