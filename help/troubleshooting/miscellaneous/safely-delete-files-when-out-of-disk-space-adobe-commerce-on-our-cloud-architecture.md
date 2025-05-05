---
title: Suppression sécurisée de fichiers lorsque le disque manque d’espace dans Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit une solution pour lorsque vous êtes à court d’espace disque et que vous devez supprimer des fichiers en toute sécurité. Avant d’envisager cette action, consultez [Gérer l’espace disque](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#no-space-left) dans notre documentation destinée aux développeurs. Si les étapes de cet article ne vous conviennent pas ou ne résolvent pas le problème, passez en revue les étapes de cet article.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Suppression sécurisée de fichiers lorsque le disque manque d’espace dans Adobe Commerce sur l’infrastructure cloud

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.2 - 2.4.7
* Ceci est spécifique aux grappes Pro dédiées. Les environnements de démarrage et d’intégration sont un noeud unique et ne possèdent pas le répertoire `/data/exports`.

## Signes de faible espace disque

Les signaux qui manquent d’espace disque peuvent être bloqués lors du déploiement, des avertissements sur le disque et des performances médiocres.
Pour voir la quantité d’espace disque utilisée par le système de fichiers, exécutez la commande suivante dans l’interface de ligne de commande/le terminal :

`df -h`


## Comment supprimer des fichiers en toute sécurité pour augmenter l’espace disque

Vous pouvez supprimer des fichiers des points de montage de l’application, de votre chemin `/app` ou via `/mnt/shared`. Il existe deux manières différentes d’accéder aux mêmes fichiers.

>[!WARNING]
>
>**Ne modifiez jamais ou ne supprimez jamais le contenu de`/data/exports`**.
>
>`/data/exports` est le stockage sous-jacent derrière le système de fichiers partagé et il est géré par GlusterFS.
>
>Le système de fichiers contient non seulement le contenu du fichier, mais aussi des métadonnées sur l’état du système de fichiers pour permettre la synchronisation > entre les noeuds de la grappe. **La modification ou la suppression de fichiers directement dans ce système de fichiers corrompt le système de fichiers partagé >et nécessite des réparations importantes ou la récupération de données.**

Pour localiser les fichiers les plus volumineux pouvant être pertinents pour l’effacement, exécutez la commande suivante (sur les projets volumineux ou occupés, il peut s’écouler jusqu’à une heure) :

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

La sortie de la commande contiendra une liste des fichiers et répertoires les plus volumineux, avec leurs tailles spécifiées.

## Lecture connexe

Dans notre base de connaissances de soutien :

* [Augmentation de l’espace disque pour l’environnement d’intégration sur Cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Espace disque faible](/help/troubleshooting/miscellaneous/low-disk-space.md)

Dans notre documentation destinée aux développeurs :

* [Gérer l’espace disque](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
