---
title: Demandes de capacité de survol des vacances pour Adobe Commerce sur notre infrastructure cloud
description: Pendant la période de pointe des ventes des fêtes (de la mi-novembre à la mi-janvier environ), Adobe recommande que tous les commerçants Adobe Commerce hébergés sur notre infrastructure cloud se préparent à une augmentation du trafic.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: dfd3f788f42677b631ffb5b3153a1c79c2cc1ca3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Demandes de capacité de survol des vacances pour Adobe Commerce sur notre infrastructure cloud

Pendant la période de pointe des ventes des fêtes (de la mi-novembre à la mi-janvier environ), Adobe recommande que tous les commerçants Adobe Commerce hébergés sur notre infrastructure cloud se préparent à une augmentation du trafic.

**Planification et estimation du trafic**

Nous recommandons à tous les commerçants Adobe Commerce sur notre infrastructure cloud [d’utiliser cet ensemble de recommandations sur la manière d’estimer le trafic en haute saison ;](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) pour la saison de vente maximale des fêtes chaque année.

Une fois que vous avez terminé l’estimation recommandée, si votre équipe a identifié des dates pour lesquelles vous pensez avoir besoin de capacité supplémentaire, passez à l’étape suivante pour plus d’informations sur la manière de demander une capacité de survol.

**Afficher l’historique de vos upgrades**

Vous pouvez afficher l’historique des redimensionnements demandés dans votre [Portail de projet (interface utilisateur d’intégration)](https://devdocs.magento.com/cloud/onboarding/onboarding-tasks.html), sous **Projet** > **Services** > **Suivi de l’utilisation du processeur**.
Les informations suivantes sont disponibles pour chaque requête de redimensionnement :

* **Date de début de la taille**: date de la requête de mise à niveau.
* **Date de fin de la taille**: date à laquelle la grappe a été renvoyée à la taille précédente.
* **vCPU Size**: taille de la grappe après la mise à niveau.
* **Jours d’utilisation**: pendant le nombre de jours pendant lesquels la grappe a été mise à niveau.
* **Période vCPU**: modification de la taille du processeur virtuel en fonction du nombre de jours pendant lesquels il a été utilisé. (par exemple, la taille du processeur virtuel de 192 sur 25 jours est égale à 4 800).

**Demande de capacité de survol**

Les commerçants Adobe Commerce de notre infrastructure cloud qui prévoient un besoin de capacité supplémentaire pendant la période des fêtes doivent [envoyer un ticket d’assistance de capacité de surge ;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) via notre [Centre d’aide](/help/overview.md), indiquant les dates et les besoins en capacité attendus dans le ticket. Veuillez noter que l’augmentation de la capacité nécessitera l’utilisation de votre capacité de surcharge sous licence.

**Nous vous recommandons d’envoyer ces tickets au moins 48 heures ouvrables à l’avance, au moment où la capacité est nécessaire. Nous vous recommandons également de placer autant d’avance que possible les demandes pour la période Black Friday/Cyber Monday, dans la mesure où la capacité pendant cette période est limitée.**


**Plus d’aide ?**

Besoin d’informations supplémentaires sur la préparation du trafic en haute saison ? Les commerçants Adobe Commerce de notre infrastructure cloud peuvent contacter leur équipe de compte d’Adobe pour obtenir de l’aide, une stratégie et des conseils de planification en vue de préparer une saison de pointe réussie. Nous vous recommandons également de consulter la [Blog du Magento](https://magento.com/blog) pour obtenir des conseils sur la stratégie tout au long de l’année.

## Ressources pour revoir vos capacités

Dans notre base de connaissances de soutien :

* [Calcul de l’allocation du processeur pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Vérifiez si la mise à niveau des instances de l’hôte est nécessaire pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Vérification de la configuration du processeur de l’hôte pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identifier et mesurer les pannes d’Adobe Commerce sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
