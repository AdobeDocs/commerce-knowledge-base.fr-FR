---
title: Adobe Commerce [!DNL crons] désactivé sans intervention
description: Utilisez cet article pour résoudre le problème de . [!DNL crons] sont désactivées sans intervention.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons désactivés sans intervention

Cet article fournit une solution pour le moment où [!DNL crons] sont désactivées sans intervention.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problème

Votre [!DNL crons] sont désactivées après le déploiement.

<u>Étapes à reproduire</u>:

Déployez .

<u>Résultat attendu</u>:

Votre [!DNL crons] sont en cours d’exécution.

<u>Résultat réel</u>:

Votre [!DNL crons] sont désactivées après le déploiement.

## Cause

Un problème avec la variable [!DNL OPcache] paramètres.

## Solution

Mettre à niveau [!DNL ECE Tools] vers la dernière version [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Lecture connexe

* [Lenteur des performances, lenteur et longue exécution [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) dans notre base de connaissances de soutien.
* [[!DNL Cron] les tâches verrouillent les tâches d’autres groupes.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) dans notre base de connaissances de soutien.
* [[!DNL Cron] La tâche est bloquée dans l’état &quot;running&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) dans notre base de connaissances de soutien.
