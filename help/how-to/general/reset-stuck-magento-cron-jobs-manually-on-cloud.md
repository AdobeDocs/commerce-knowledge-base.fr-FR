---
title: Réinitialiser manuellement Adobe Commerce bloqué sur les tâches cron de l’infrastructure cloud
description: Les tâches cron d’Adobe Commerce sur l’infrastructure cloud ne se terminent pas à s’exécuter, restent bloquées et empêchent l’exécution d’autres tâches cron. Cet article explique comment réinitialiser manuellement les tâches cron bloquées.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Réinitialiser manuellement Adobe Commerce bloqué sur les tâches cron de l’infrastructure cloud

Les tâches cron d’Adobe Commerce sur l’infrastructure cloud ne se terminent pas à s’exécuter, restent bloquées et empêchent l’exécution d’autres tâches cron. Cet article explique comment réinitialiser manuellement les tâches cron bloquées.

Utilisez cette commande avec précaution. Il est recommandé de lire le [Réinitialisation des tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) pour plus d’informations.

## Étapes

>[!INFO]
>
>De [CEE-Outils v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) vous pouvez réinitialiser manuellement les tâches cron bloquées à l’aide d’une commande d’interface de ligne de commande via un accès SSH.

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Exécutez la commande suivante : `./vendor/bin/ece-tools cron:unlock`

## Avertissements

* La commande réinitialise **all** les tâches cron, y compris celles qui sont en cours d’exécution ; **l’utiliser dans des cas exceptionnels uniquement**.
* Évitez d’utiliser cette solution lorsque les indexeurs sont en cours d’exécution.

## Lisez-le dans notre base de connaissances d&#39;assistance :

[Réinitialisation des tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
