---
title: Dépannage du montage /tmp complet pour Adobe Commerce
description: Cet article fournit une solution pour le cas où le montage `/tmp` est plein, où le site est en panne et où vous ne pouvez pas effectuer de SSH dans un nœud.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Dépannage du montage /tmp complet pour Adobe Commerce

Cet article fournit une solution pour le cas où le montage `/tmp` est saturé, où le site est en panne et où vous ne pouvez pas effectuer de SSH sur un nœud.

## Produits et versions concernés

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problème

Le montage `/tmp` étant saturé, divers symptômes peuvent se produire, notamment les erreurs suivantes :

* *SQLSTATE[HY000] : Erreur générale : 3 Erreur lors de l&#39;écriture du fichier*
* *Code d&#39;erreur : 28*
* *Pas d&#39;espace restant sur l&#39;appareil (28)*
* *error session_start(): failed: No space left on device*
* *ERREUR 1 (HY000) : impossible de créer/écrire dans le fichier &#39;/tmp/*
* *Erreur SQL : 3, SQLState : HY000*
* *Erreur générale : 1 021 Disque plein (/tmp)*
* *Impossible d’accéder au nœud via SSH:*
  *bash: impossible de créer un fichier temporaire pour here-document: Il ne reste plus d&#39;espace sur l&#39;appareil*
* *errno : 28 « Aucun espace restant sur l&#39;appareil »*
* *mysqld : le disque est en pleine écriture &#39;/tmp&#39;*
* *[ERROR] mysqld : disque plein (/tmp)*
* *SQLSTATE[HY000] : erreur générale : 1 impossible de créer/écrire dans le fichier &#39;/tmp/&#39;*
* *SQLSTATE[HY000] : Erreur générale : 23 ressources insuffisantes lors de l&#39;ouverture du fichier &#39;/tmp/&#39;*
* *Code d’erreur : 24 « Trop de fichiers ouverts »*
* *Erreur reçue : 23 : ressources insuffisantes lors de l’ouverture du fichier*


<u>Procédure à suivre :</u>

Pour vérifier si le montage `/tmp` est plein, dans l’interface de ligne de commande, passez à `/tmp` et exécutez la commande suivante :

```bash
 df -h
```

<u>Résultat attendu </u> :

Moins de 80 %.

<u>Résultat réel</u> :

Environ 100 %.

## Cause

Le montage `/tmp` comporte trop de fichiers, ce qui peut être dû aux éléments suivants :

* Requêtes SQL incorrectes générant des tables temporaires volumineuses et/ou trop nombreuses.
* Services écrivant dans le répertoire `/tmp`.
* Sauvegardes/vidages de base de données laissés dans le répertoire `/tmp`.

## Solution

Il y a des choses que vous pouvez faire pour libérer de l&#39;espace une fois, et il y a des pratiques exemplaires qui empêcheraient les `\tmp` d&#39;être pleines.

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

Vérifiez que le pourcentage d’utilisation est &lt; 70 %. Les nœuds sont corrélés aux fichiers. Si vous supprimez des fichiers de la partition, vous libérez des inodes.

### Vérifier et libérer de l&#39;espace de stockage

Plusieurs services peuvent enregistrer des fichiers dans `/tmp`.

#### Vérifier et libérer de l&#39;espace MySQL

Suivez les instructions de la section [L’espace disque MySQL est faible sur Adobe Commerce sur l’infrastructure cloud > Vérifier et libérer de l’espace de stockage](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806#check-and-free-up-storage-space) dans notre base de connaissances du support.

#### Vérifier les vidages de tas d’Elasticsearch

>[!WARNING]
>
>Les images mémoire contiennent des informations de journalisation qui peuvent s’avérer utiles pour enquêter sur les problèmes. Envisagez de les stocker dans un emplacement distinct pendant au moins 10 jours.

Supprimez les vidages de tas (`*.hprof`) à l’aide du shell système :

```bash
find /tmp/*.hprof -type f -delete
```

Si vous ne disposez pas des autorisations nécessaires pour supprimer les fichiers créés par un autre utilisateur (dans ce cas, Elasticsearch), mais que vous constatez que les fichiers sont volumineux, veuillez [créer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour les gérer.

#### Vérifier les sauvegardes/vidages de bases de données

>[!WARNING]
>
>Les sauvegardes de base de données sont généralement créées dans un but précis. Si vous ne savez pas si le fichier est toujours nécessaire, envisagez de le déplacer vers un emplacement distinct au lieu de le supprimer.

Recherchez `/tmp` fichiers `.sql` ou `.sql.gz` et nettoyez-les. Ils peuvent avoir été créés par ece-tools pendant la sauvegarde ou lors de la création manuelle de vidages de base de données à l&#39;aide de l&#39;outil `mysqldump`.

### Bonnes pratiques

Pour éviter tout problème lié au remplissage du `/tmp`, suivez ces recommandations :

* N’utilisez pas MySQL pour la recherche. Elasticsearch for search élimine généralement la nécessité de créer des tables temporaires volumineuses. Voir [Configuration d’Adobe Commerce pour utiliser Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine) dans notre documentation destinée aux développeurs.
* Évitez d’exécuter la requête `SELECT` sur des colonnes sans index, car cela consomme une grande quantité d’espace disque temporaire. Vous pouvez également ajouter les index.
* Créez un cron pour nettoyer les `/tmp` en exécutant la commande suivante dans l’interface de ligne de commande :

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Lecture connexe

[L’espace disque MySQL est faible sur Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806) dans notre base de connaissances d’assistance.
