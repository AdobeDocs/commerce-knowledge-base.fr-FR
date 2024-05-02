---
title: Résolution des problèmes /tmp de montage complet pour Adobe Commerce
description: Cet article fournit une solution pour lorsque le montage `/tmp` est plein, que le site peut être hors service et que vous ne pouvez pas SSH dans un noeud.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Résolution des problèmes /tmp de montage complet pour Adobe Commerce

Cet article fournit une solution pour lorsque la variable `/tmp` Le montage est plein, le site peut être en panne et vous ne pouvez pas SSH dans un noeud.

## Produits et versions concernés

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problème

La variable `/tmp` Le mode de montage étant complet, il se peut que plusieurs symptômes se produisent, notamment les erreurs suivantes :

* *SQLSTATE[HY00]: Erreur générale : 3 Erreur lors de l’écriture du fichier*
* *Code d’erreur : 28*
* *Aucun espace laissé sur l’appareil (28)*
* *error session_start() : échec : aucun espace laissé sur l’appareil*
* *ERREUR 1 (HY000) : impossible de créer/écrire dans le fichier &#39;/tmp/*
* *Erreur SQL : 3, SQL : HY000*
* *Erreur générale : 1021 disque plein (/tmp)*
* *Impossible d’accéder au noeud via SSH :*
  *bash : impossible de créer un fichier temporaire pour le document ici : aucun espace ne reste sur l’appareil*
* *erreur : 28 &quot;Aucun espace laissé sur l’appareil&quot;*
* *mysqld : le disque est en écriture complète &#39;/tmp&#39;*
* *[ERROR] mysqld : disque plein (/tmp)*
* *SQLSTATE[HY00]: Erreur générale : 1 Impossible de créer/écrire dans le fichier &#39;/tmp/&#39;*
* *SQLSTATE[HY00]: Erreur générale : 23 ressources épuisées lors de l&#39;ouverture du fichier &#39;/tmp/&#39;*
* *Errcode : 24 &quot;Trop de fichiers ouverts&quot;*
* *Erreur de récupération : 23 : ressources indisponibles lors de l’ouverture du fichier*


<u>Étapes à reproduire :</u>

Pour vérifier si la variable `/tmp` Le montage est, dans l’interface de ligne de commande, passez à `/tmp` et exécutez la commande suivante :

```bash
 df -h
```

<u>Résultat attendu</u>:

Moins de 80%.

<u>Résultat réel</u>:

Environ 100%.

## Cause

La variable `/tmp` Le montage contient trop de fichiers, ce qui peut être dû à :

* Requêtes SQL incorrectes générant des tables temporaires volumineuses et/ou trop nombreuses.
* Services écrivant sur la `/tmp` répertoire .
* Sauvegardes/vidages de base de données laissés dans la `/tmp` répertoire .

## Solution

Il y a des choses que vous pouvez faire pour libérer de l&#39;espace une fois, et il y a des bonnes pratiques qui empêcheraient `\tmp` de devenir complet.

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

Vérifiez que le taux d’utilisation est inférieur à 70 %. Les noeuds sont corrélés avec des fichiers. Si vous supprimez des fichiers de la partition, vous libérez des informations.

### Vérifier et libérer l’espace de stockage

Plusieurs services peuvent enregistrer des fichiers dans `/tmp`.

#### Vérifier et libérer l’espace MySQL

Suivez les instructions de la section [L’espace disque MySQL est faible sur Adobe Commerce sur l’infrastructure cloud > Vérifier et libérer l’espace de stockage](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) dans notre base de connaissances de soutien.

#### Vérification des vidages Elasticsearch

>[!WARNING]
>
>Les images mémoire contiennent des informations de journalisation qui peuvent s’avérer utiles pour enquêter sur des problèmes. Envisagez de les stocker dans un emplacement distinct pendant au moins 10 jours.

Suppression des vidages (`*.hprof`) à l’aide du shell système :

```bash
find /tmp/*.hprof -type f -delete
```

Si vous ne disposez pas des autorisations nécessaires pour supprimer des fichiers créés par un autre utilisateur (dans ce cas, Elasticsearch), mais que vous constatez que les fichiers sont volumineux, veuillez [créer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour les traiter.

#### Vérification des vidages/sauvegardes de base de données

>[!WARNING]
>
>Les sauvegardes de la base de données sont généralement créées à des fins spécifiques. Si vous ne savez pas si le fichier est toujours nécessaire, envisagez de le déplacer vers un emplacement distinct au lieu de le supprimer.

Vérifier `/tmp` pour `.sql` ou `.sql.gz` et les nettoyer. Ils peuvent avoir été créés par des outils de données lors de la sauvegarde ou lors de la création manuelle de vidages de base de données à l’aide de la fonction `mysqldump` outil.

### Bonnes pratiques

Pour éviter tout problème avec `/tmp` étant complet, suivez les recommandations suivantes :

* N’utilisez pas MySQL pour la recherche. L’Elasticsearch pour la recherche élimine généralement la nécessité de la plupart des créations de tables temporaires volumineuses. Voir [Configuration d’Adobe Commerce pour l’utilisation d’Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) dans notre documentation destinée aux développeurs.
* Évitez d’exécuter la variable `SELECT` requête sur les colonnes sans index, car cela nécessite un grand volume d’espace disque temporaire. Vous pouvez également ajouter les index.
* Création d’un cron à nettoyer `/tmp` en exécutant la commande suivante dans l’interface de ligne de commande :

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Lecture connexe

[L’espace disque MySQL est faible sur Adobe Commerce sur l’infrastructure cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) dans notre base de connaissances de soutien.
