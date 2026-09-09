---
title: ' [!DNL crons] désactivé sans intervention'
description: Utilisez cet article pour résoudre le problème de désactivation  [!DNL crons]  sans intervention.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 6bff1d7a0578ceb8ea17dff347b1bcd4f0068e7a
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Adobe Commerce crons désactivé sans intervention

Cet article fournit une solution pour les [!DNL crons] désactivés sans intervention.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problème

Vos [!DNL crons] sont désactivées après le déploiement.

<u>Procédure à suivre </u> :

Déployer.

<u>Résultat attendu </u> :

Vos [!DNL crons] sont en cours d’exécution.

<u>Résultat réel</u> :

Vos [!DNL crons] sont désactivées après le déploiement.

## Cause

Un problème lié aux paramètres [!DNL OPcache].

## Solution

Mettez à niveau [!DNL ECE Tools] vers la dernière version [2002.1.13](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Lecture connexe

* [Performances lentes, exécution lente et longue durée [!DNL crons]](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-42802) dans notre base de connaissances en matière d’assistance.
* [[!DNL Cron] les tâches verrouillent les tâches d’autres groupes](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=fr) dans notre base de connaissances du support.
* [[!DNL Cron] la tâche est bloquée au statut « en cours d’exécution »](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=fr) dans notre base de connaissances d’assistance.
