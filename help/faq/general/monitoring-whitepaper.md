---
title: Fiche d'information sur le suivi pour  [!DNL Adobe Commerce on cloud pro infrastructure]
description: Ce document fournit des informations sur la surveillance et les notifications de l’infrastructure Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Fiche d’information sur le suivi des [!DNL Adobe Commerce on cloud pro infrastructure]

Ce document fournit des informations sur la surveillance et les notifications de l’infrastructure Adobe Commerce.

La surveillance permet aux commerçants, aux intégrateurs système et aux équipes internes d’Adobe de résoudre les problèmes de disponibilité du site et d’espace disque insuffisant.

## Dépannage et résolution des problèmes

Les instances Adobe Commerce contiennent généralement du code personnalisé et des configurations. Adobe ne prend pas en charge ni ne résout les problèmes liés au code personnalisé et aux configurations. Adobe aide les commerçants à résoudre les problèmes et à les identifier dans notre base de connaissances. Il fournit également des solutions recommandées et des bonnes pratiques de prévention et de résolution. Nous encourageons les commerçants et les partenaires à utiliser les tableaux ci-dessous pour comprendre ce qui est surveillé et qui est responsable de la résolution.

Lorsque les notifications sont déclenchées, l’équipe d’assistance Adobe Commerce triera le problème. Dans le cadre du triage, les journaux d’erreurs et d’autres ressources sont analysés. Selon le triage, des tickets d’assistance [!DNL Zendesk] supplémentaires sont créés pour les commerçants ou les partenaires (en cas de mises à jour personnalisées) ou pour les équipes internes d’Adobe afin de résoudre le problème.

## Adobe Commerce : surveillance par défaut

Les événements ci-dessous sont surveillés et l’équipe d’Adobe Commerce prend les mesures nécessaires pour résoudre et communiquer les problèmes identifiés.

## Surveillance de la disponibilité du site

| Disponibilité du site | Description |
|------------|------------|
| **Objectif de surveillance** | Pour suivre la disponibilité du site. |
| **Instrumenté le** | [!DNL URL] unique sélectionné pour une [!DNL SLA] élevée. |
| **Description** | La disponibilité du site est déterminée en fonction des seuils configurés autour de la mesure. Une notification de panne du site est déclenchée si la vérification échoue pendant 10 minutes et qu’aucun déploiement actif n’est en cours. |
| **Destinataire de la notification** | Commerçant/partenaire et Adobe. |
| **Action d’Adobe** | Responsable du tri et de la résolution du problème sur l’infrastructure d’Adobe Commerce. |
| **Action du commerçant** | Responsable de la résolution du problème s’il est causé par des modifications ou un code personnalisé introduit par le commerçant/partenaire. Pour le dépannage, reportez-vous à : [Résolution des problèmes de panne du site](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=fr). |

## Surveillance de l’espace disque

| Surveillance de l’espace disque | Description |
|------------|------------|
| **Objectif de surveillance** | Pour suivre l’utilisation de l’espace disque. |
| **Instrumenté le** | Partitions de disque [!DNL MySQL] et de disque Media. |
| **Mesure** | L&#39;espace disque disponible est surveillé chaque minute sur l&#39;hôte. L’avertissement est déclenché s’il ne reste que 5 % ou 2 Go d’espace libre. Le seuil critique défini sur l’espace libre restant est de 2 % ou 1 Go. |
| **Description** | La notification est envoyée en fonction des seuils configurés autour de l’espace disque libre pour l’hôte. Un espace disque supplémentaire est automatiquement ajouté une fois au montage approprié ([!DNL MySQL] ou média) pour éviter une panne du site et pour donner au commerçant le temps d’effacer l’espace disque et/ou d’identifier et de résoudre tout code ou journal entraînant une augmentation rapide de l’utilisation du disque. |
| **Destinataire de la notification** | Commerçant/partenaire et Adobe. |
| **Action d’Adobe** | Augmentez automatiquement le ticket d’assistance et de l’espace disque supplémentaire est automatiquement ajouté au montage approprié ([!DNL MySQL] ou média) pour éviter une panne du site. |
| **Action du commerçant** | Pour recevoir des alertes d’espace disque de niveau d’avertissement, reportez-vous à : <ul><li>[[!DNL Managed alerts for Adobe Commerce] : alerte d’avertissement de disque](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert)</li><li>[[!DNL Managed alerts for Adobe Commerce] : alerte critique du disque](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert) </li></ul> |
