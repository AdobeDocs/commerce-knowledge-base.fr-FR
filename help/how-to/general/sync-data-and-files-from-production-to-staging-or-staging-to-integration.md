---
title: Synchronisation des données et des fichiers de la production vers l’évaluation ou l’évaluation vers l’intégration
description: Cet article explique comment synchroniser votre environnement de production et passer à l’évaluation sur Adobe Commerce sur l’infrastructure cloud ; cela n’est pas possible.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: ef294ddc9c4a12b06ce7738cb4702253dd892f3b
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Synchronisation des données et des fichiers de la production vers l’évaluation ou l’évaluation vers l’intégration

Cet article explique comment synchroniser votre environnement de production et passer à l’évaluation sur Adobe Commerce sur l’infrastructure cloud ; cela n’est pas possible via l’interface utilisateur ou l’interface de ligne de commande de Magento-cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.x, 2.4.x

## Pour synchroniser les données d’un environnement vers un autre

Pour synchroniser les données, vous devez vider manuellement la base de données de l’environnement source. Pour transférer des données vers un autre environnement, vous devez ensuite charger la vidange source dans l&#39;environnement cible et l&#39;importer. Pour plus d’informations, voir [Importation du code Adobe Commerce dans un projet Cloud > Importation de la base de données Adobe Commerce](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html) dans notre documentation destinée aux développeurs.

Pour l’architecture de plan d’Adobe Commerce on Cloud Infrastructure Pro, vous pouvez également vous synchroniser de l’évaluation et de la production à votre branche principale d’intégration. Cette synchronisation extrait et envoie uniquement le code, et non les données. Pour synchroniser les données, vous devez vider les données de la base de données et les transmettre à la base de données d’un autre environnement.

>[!WARNING]
>
>La synchronisation de la base de données ne peut pas être effectuée dans les grappes d’évaluation et de production Pro.

## Pour synchroniser des fichiers d’un environnement à un autre

Pour synchroniser les fichiers d&#39;un environnement à un autre, utilisez la commande `rsync`. Pour plus d’informations, voir [Déploiement du code et migration des fichiers et données statiques > Migration des fichiers à l’aide de rsync](https://devdocs.magento.com/cloud/live/stage-prod-migrate.html#migrate-files-using-rsync) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>Si vous souhaitez synchroniser le code de l’intégration à l’évaluation, vous devez le faire à partir de la branche d’intégration. Pour connaître les étapes, voir [Synchronisation à partir du parent de l’environnement](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) dans notre documentation destinée aux développeurs.
