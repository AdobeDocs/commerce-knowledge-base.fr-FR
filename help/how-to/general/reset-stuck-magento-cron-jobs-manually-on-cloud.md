---
title: Réinitialiser manuellement les tâches cron bloquées sur l’infrastructure cloud
description: Les tâches cron d’Adobe Commerce sur l’infrastructure cloud ne finissent pas de s’exécuter, se bloquent et empêchent l’exécution d’autres tâches cron. Cet article explique comment réinitialiser manuellement les tâches cron bloquées.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# Réinitialiser manuellement les tâches cron bloquées sur l’infrastructure cloud

Les tâches cron d’Adobe Commerce sur l’infrastructure cloud ne finissent pas de s’exécuter, se bloquent et empêchent l’exécution d’autres tâches cron. Cet article explique comment réinitialiser manuellement les tâches cron bloquées.

Utilisez cette commande avec précaution ! Nous vous recommandons de lire l’article [Réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=fr) dans notre base de connaissances d’assistance pour plus d’informations.

## Étapes

>[!INFO]
>
>Depuis [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=fr#v2002.0.4) vous pouvez réinitialiser manuellement les tâches cron bloquées à l&#39;aide d&#39;une commande CLI via un accès SSH.

1. [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr).
1. Exécutez la commande suivante : `./vendor/bin/ece-tools cron:unlock`

## Avertissements

* La commande réinitialise **toutes** les tâches cron, y compris celles en cours d’exécution ; **utilisez-la uniquement dans des cas exceptionnels**.
* Évitez d’utiliser cette solution lorsque les indexeurs sont en cours d’exécution.

## Lisez-le dans notre base de connaissances d’assistance :

[Réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=fr)
