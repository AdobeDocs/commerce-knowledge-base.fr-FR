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

Utilisez cette commande avec précaution. Pour plus d’informations, nous vous recommandons de lire l’article [Réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=fr) dans notre base de connaissances d’assistance.

## Étapes

>[!INFO]
>
>À partir de [CEE-Outils v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=fr#v2002.0.4), vous pouvez réinitialiser manuellement les tâches cron bloquées à l’aide d’une commande d’interface de ligne de commande via un accès SSH.

1. [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr).
1. Exécutez cette commande : `./vendor/bin/ece-tools cron:unlock`

## Avertissements

* La commande réinitialise **toutes** tâches cron, y compris celles en cours d’exécution ; **utilisez-la dans des cas exceptionnels uniquement**.
* Évitez d’utiliser cette solution lorsque les indexeurs sont en cours d’exécution.

## Lisez-le dans notre base de connaissances d&#39;assistance :

[Réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=fr)
