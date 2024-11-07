---
title: Adobe Commerce [!DNL crons] désactivé sans intervention
description: Utilisez cet article pour résoudre le problème de désactivation de [!DNL crons] sans intervention.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons désactivés sans intervention

Cet article fournit une solution lorsque [!DNL crons] sont désactivés sans intervention.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problème

Vos [!DNL crons] sont désactivés après le déploiement.

<u>Étapes à reproduire</u> :

Déployez .

<u>Résultat attendu</u> :

Vos [!DNL crons] sont en cours d’exécution.

<u>Résultat réel</u> :

Vos [!DNL crons] sont désactivés après le déploiement.

## Cause

Problème avec les paramètres [!DNL OPcache].

## Solution

Mettez à niveau [!DNL ECE Tools] vers la dernière version [2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Lecture connexe

* [ ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) dans notre base de connaissances de support. Performances lentes, lentes et longues. [!DNL crons]
* [[!DNL Cron] tâches verrouillent les tâches d’autres groupes](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) dans notre base de connaissances de support.
* [[!DNL Cron] job est bloqué dans l’état &quot;running&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) dans notre base de connaissances de support.
