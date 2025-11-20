---
title: Demandes de capacité de pointe pendant les fêtes pour Adobe Commerce sur notre infrastructure cloud
description: Pendant la haute saison des ventes de fin d’année (entre mi-novembre et mi-janvier environ), Adobe recommande à tous les commerçants Adobe Commerce hébergés sur notre infrastructure cloud de se préparer à un trafic accru.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 9cd7eeb6af379fa94e234bb677b532051079995c
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Demandes de capacité de pointe pendant les fêtes pour Adobe Commerce sur notre infrastructure cloud

Pendant la haute saison des ventes de fin d’année (entre mi-novembre et mi-janvier environ), Adobe recommande à tous les commerçants Adobe Commerce hébergés sur notre infrastructure cloud de se préparer à un trafic accru.

Pour obtenir une liste de contrôle complète et intersolutions ainsi que des bonnes pratiques pour préparer vos systèmes et vos équipes à la saison de pointe, consultez le [Guide de préparation des vacances unifiées Adobe DX](https://experienceleague.adobe.com/en/docs/support-resources/data-sheets/unified-holiday-readiness).

**Planification et estimation du trafic**

Nous recommandons à tous les commerçants Adobe Commerce de notre infrastructure cloud [d’utiliser cet ensemble de recommandations sur la manière d’estimer le trafic de haute saison](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) pour la haute saison des ventes de vacances, chaque année.

Une fois que vous avez terminé l’estimation recommandée, si votre équipe a identifié des dates pour lesquelles vous pensez avoir besoin de capacité supplémentaire, passez à l’étape suivante pour obtenir des informations sur la manière de demander une capacité de pointe.

**Voir l&#39;historique de vos uptailles**

Vous pouvez afficher l’historique des redimensionnements demandés en demandant les informations à votre **CSM (Customer Success Manager)**.
Les informations suivantes sont disponibles pour chaque demande de redimensionnement :

* **Date de début de la taille** : date de la demande de mise à niveau.
* **Date de fin de la taille** : date à laquelle le cluster a été rétabli à sa taille précédente.
* **taille du processeur virtuel** : taille du cluster après la mise à niveau.
* **Utilisation en jours** : nombre de jours pendant lesquels le cluster a été mis à niveau.
* **Période vCPU** : modification de la taille du vCPU en fonction du nombre de jours d&#39;utilisation. (par exemple, la taille de vCPU 192 par 25 jours est égale à 4 800).

**Demande de capacité de pointe**

Les commerçants Adobe Commerce de notre infrastructure cloud qui prévoient un besoin de capacité supplémentaire pendant la saison des fêtes doivent [envoyer un ticket d’assistance pour la capacité de pointe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) via notre [Centre d’aide](/help/overview.md), en indiquant les dates et les besoins en capacité prévus dans le ticket. Notez qu’une capacité accrue nécessitera l’utilisation de votre capacité excédentaire sous licence.

**Nous vous recommandons d’envoyer ces billets au moins 48 heures ouvrables avant le moment où la capacité est nécessaire ; et de recommander également que les demandes pour la période Black Friday / Cyber Monday soient placées aussi longtemps à l’avance que possible, car la capacité pendant cette période est limitée.**


**Plus d’aide ?**

Vous avez besoin de plus de conseils sur la préparation du trafic en haute saison ? Les commerçants Adobe Commerce de notre infrastructure cloud peuvent contacter leur équipe de compte Adobe pour obtenir de l’aide, des conseils stratégiques et de planification afin de se préparer à une saison de pointe réussie. Nous vous recommandons également de consulter le [blog Magento](https://magento.com/blog) pour obtenir des conseils stratégiques tout au long de l’année.

## Ressources sur la révision de votre capacité

Dans notre base de connaissances du support :

* [calcul de l’allocation de CPU pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Vérifiez si une mise à niveau des instances de l’hôte est nécessaire pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Vérifiez la configuration CPU de l’hôte pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identifier et mesurer les pannes pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
