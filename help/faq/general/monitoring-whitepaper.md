---
title: Surveillance de la feuille de faits pour [!DNL Adobe Commerce on cloud pro infrastructure]
description: Ce document fournit des informations sur la surveillance et les notifications de l’infrastructure Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Surveillance de la feuille de faits pour [!DNL Adobe Commerce on cloud pro infrastructure]

Ce document fournit des informations sur la surveillance et les notifications de l’infrastructure Adobe Commerce.

La surveillance permet aux commerçants, aux intégrateurs système et aux équipes internes de l’Adobe de résoudre les problèmes de disponibilité du site et d’espace disque insuffisant.

## Résolution des problèmes

Les instances Adobe Commerce contiennent généralement du code et des configurations personnalisés. Adobe ne prend pas en charge et ne résout pas les problèmes liés au code et aux configurations personnalisés. Adobe aide les marchands à dépanner et à identifier les problèmes dans notre base de connaissances et fournit des solutions recommandées et des bonnes pratiques de prévention et de résolution. Nous encourageons les commerçants et les partenaires à utiliser les tableaux ci-dessous pour comprendre ce qui est surveillé et qui est responsable de la résolution.

Lorsque les notifications sont déclenchées, l’équipe d’assistance d’Adobe Commerce triera le problème. Dans le cadre du triage, les journaux d’erreurs et d’autres ressources sont analysés. En fonction du triage, la variable [!DNL Zendesk] les tickets d’assistance sont créés pour les commerçants ou les partenaires (en cas de mises à jour personnalisées) ou pour les équipes internes de l’Adobe afin de résoudre le problème.

## Adobe Commerce : surveillance par défaut

Les événements ci-dessous sont surveillés et l’équipe Adobe Commerce prend les mesures nécessaires pour résoudre et communiquer les problèmes identifiés.

## Surveillance de la disponibilité du site

| Disponibilité du site | Description |
|------------|------------|
| **Objectif de surveillance** | Pour suivre la disponibilité du site. |
| **Instrumenté sur** | Simple [!DNL URL] sélectionné pour élevé [!DNL SLA]. |
| **Description** | La disponibilité du site est déterminée en fonction des seuils configurés autour de la mesure. La notification de panne du site est déclenchée si la vérification échoue pendant 10 minutes et qu’aucun déploiement actif n’est en cours. |
| **Destinataire de la notification** | Marchand/Partenaire et Adobe. |
| **Action par Adobe** | Responsable du triage et de la résolution du problème concernant l’infrastructure Adobe Commerce. |
| **Action des commerçants** | Responsable de la résolution du problème en cas de modifications ou de code personnalisé introduit par le marchand/partenaire. Pour la résolution des problèmes, reportez-vous à : [Dépannage de Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Surveillance de Diskspace

| Surveillance de Diskspace | Description |
|------------|------------|
| **Objectif de surveillance** | Pour suivre l’utilisation de l’espace de disque. |
| **Instrumenté sur** | [!DNL MySQL] Partitions de disque et de disque Media. |
| **Mesure** | L&#39;espace disque disponible est surveillé toutes les minutes sur l&#39;hôte. Un avertissement s’affiche si seulement 5 % ou 2 Go d’espace libre sont restants. Le seuil critique défini à l’espace libre restant est de 2 % ou 1 Go. |
| **Description** | La notification est envoyée en fonction des seuils configurés autour de l’espace de disque libre pour l’hôte. Un espace disque supplémentaire est automatiquement ajouté une fois au montage correspondant ([!DNL MySQL] ou média) pour empêcher une panne du site et donner au commerçant le temps d’effacer l’espace disque et/ou d’identifier et de résoudre tout code ou journal provoquant une augmentation rapide de l’utilisation du disque. |
| **Destinataire de la notification** | Marchand/Partenaire et Adobe. |
| **Action par Adobe** | Augmenter automatiquement le ticket de support et ajouter de l’espace disque supplémentaire au montage approprié ([!DNL MySQL] ou média) pour éviter une panne du site. |
| **Action des commerçants** | Pour recevoir des alertes d’espace disque de niveau d’avertissement en cours, reportez-vous à : <ul><li>[[!DNL Managed alerts for Adobe Commerce]: alerte d’avertissement du disque](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: alerte critique du disque](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
