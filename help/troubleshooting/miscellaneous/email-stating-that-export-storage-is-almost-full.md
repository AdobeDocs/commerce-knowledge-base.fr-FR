---
title: E-mail indiquant que le stockage des exportations est presque plein
description: Cet article fournit une solution au problème de réception d’un e-mail indiquant que le stockage des exportations est presque plein.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# E-mail indiquant que le stockage des exportations est presque plein

Cet article fournit une solution au problème de réception d’un e-mail indiquant que le stockage des exportations est presque plein.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud (toutes versions)

## Problème

Vous recevez un e-mail avec le contenu suivant, mais vous ne parvenez pas à localiser le dossier *exports* :

*Notre surveillance a détecté que le stockage « export » sur votre cluster XXX est saturé à environ 85 %.*
*Si nécessaire, veuillez consulter l’utilisation, effectuer un nettoyage ou demander une mise à niveau.*
*Notez également que nous tenterons une mise à niveau automatiquement lorsque le stockage atteindra le niveau de seuil critique.*

## Cause

L’alerte fait référence au système de fichiers de stockage de l’exportation, qui est le volume du disque sur lequel les médias et d’autres données de fichier sont stockés. Ce système de fichiers est généralement monté à l’adresse `/data/exports`. L’alerte n’indique pas la présence d’un seul répertoire littéralement nommé exports.

Pour confirmer à quoi l’alerte fait référence, vérifiez l’utilisation de l’espace de stockage des exportations :

* Exécutez `df -h | grep exports` et l’exemple de sortie suivant s’affiche :

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* Dans cet exemple, `/data/exports` est le système de fichiers d’exportation principal :

   * 50 Go au total
   * 38 Go utilisés
   * 12 Go disponibles (taux d’utilisation de 77 %)

* `/data/exports/shared` est un montage `tmpfs` (en mémoire) utilisé pour les données partagées et ne contribue pas de manière significative à la pression du disque.

Cela confirme que l’alerte est déclenchée par l’utilisation globale du disque de `/data/exports`, et non par un seul dossier nommé exports.

Si `/data/exports` affiche une utilisation élevée, les répertoires volumineux sous ce système de fichiers, tels que pub/media ou d’autres emplacements de fichiers personnalisés, sont généralement responsables de l’augmentation de l’utilisation.

## Solution

Suivez ces étapes pour examiner, nettoyer et valider l’utilisation du stockage des exportations.

1. Exécutez la `df -h | grep exports` de commande pour vérifier l’utilisation actuelle du système de fichiers de stockage d’export. Consultez la colonne **Utiliser%** pour `/data/exports` :

   * Si l’utilisation est comprise entre 70 et 85 %, commencez à planifier le nettoyage.
   * Si l’utilisation est supérieure à 90 %, prenez immédiatement des mesures pour éviter les échecs d’écriture ou l’impact sur le service.

1. Identifiez les répertoires consommant de l’espace disque important sous `/data/exports` en exécutant :

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   Les emplacements standard où le stockage de fichiers est susceptible d’être plein sont les dossiers `pub/media/catalog/product/cache` ou `var/log`.

1. Nettoyez les fichiers en fonction de l’environnement :

   * Supprimez d’abord les fichiers d’exportation, les journaux ou les données temporaires anciens ou inutilisés.
   * Dans les environnements hors production, vous pouvez généralement supprimer plus agressivement les médias de test ou les anciens artefacts.
   * Dans les environnements de production, assurez-vous de consulter votre équipe avant de supprimer des médias ou des fichiers critiques.

1. Après le nettoyage, exécutez la `df -h | grep exports` de commande suivante pour confirmer que la valeur **Use%** pour `/data/exports` a chuté à un niveau de fonctionnement sûr.

## Lectures connexes

[Consultez les clusters dédiés](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) dans notre base de connaissances sur le support.
