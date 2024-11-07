---
title: "Alertes gérées sur Adobe Commerce : alerte critique du processeur"
description: Cet article décrit les étapes de dépannage lorsque vous recevez une alerte critique du processeur pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alerte critique du processeur

Cet article décrit les étapes de dépannage lorsque vous recevez une alerte critique du processeur pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![alerte critique sur le disque](assets/cpu-critical-magento-managed.png){width="500"}

## Produits et versions concernés

Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro

## Problème

Vous recevrez une alerte gérée dans New Relic si vous avez signé jusqu’à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe Commerce pour fournir aux clients un ensemble standard d’informations provenant de l’assistance et de l’ingénierie.

<u>**Do!**</u> :

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour les étapes, reportez-vous au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour les étapes, reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u>**Don&#39;t !**</u> :

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez les tâches administratives principales (c’est-à-dire l’administrateur Commerce, les imports/exports de données).
* Effacez le cache.

Votre site peut ne plus être réactif (si vous n’êtes pas déjà en panne) si vous effectuez l’une des actions &quot;Ne pas&quot; avant d’avoir enquêté et résolu la cause de l’alerte.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

>[!WARNING]
>
>Puisqu’il s’agit d’une alerte critique, il est vivement recommandé de terminer l’**étape 1** avant de tenter de résoudre le problème (à partir de l’étape 2).

Vérifiez si le ticket d’assistance Adobe Commerce existe. Pour connaître les étapes, reportez-vous à la section [Suivi de vos tickets d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances d&#39;assistance. La prise en charge a peut-être reçu une alerte de seuil New Relic, créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit comporter les informations suivantes :

1. Raison de contact : sélectionnez &quot;New Relic CRITICAL alert received&quot;.
1. Description de l’alerte.
1. [Lien d’incident New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Elle est incluse dans vos [alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Utilisez la [page des transactions de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :
   * Triez les transactions par scores Apdex croissants. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. Un [score Apdex faible](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Il est généralement lié à la base de données, Redis ou PHP. Pour connaître les étapes, reportez-vous à la section New Relic [Affichage des transactions présentant le plus grand insatisfaction Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions selon le débit le plus élevé, le temps de réponse moyen le plus lent, le plus long et d’autres seuils. Pour les étapes, reportez-vous à la section New Relic [Trouver des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si vous avez encore du mal à identifier la source, utilisez la [page d’infrastructure du New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) pour identifier les services gourmands en ressources. Pour les étapes, reportez-vous à la section New Relic [Page Hôtes de surveillance de l’infrastructure > Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si vous identifiez la source, connectez-vous à l’environnement pour en savoir plus. Pour connaître les étapes à suivre, reportez-vous à la section [SSH dans votre environnement pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) de notre documentation destinée aux développeurs.
1. Si vous avez toujours du mal à identifier la source :
   * Examinez les tendances récentes pour identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
   * Pensez à rechercher et désactiver des catalogues plats. Pour les étapes, reportez-vous à la section [Cons lents, lents et à exécution longue](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) de notre base de connaissances de support.
   * Si vous pensez que vous rencontrez une attaque DDoS, essayez de bloquer le trafic de robots. Pour les étapes, reportez-vous à la section [Comment bloquer le trafic malveillant pour Adobe Commerce sur l’infrastructure cloud à un niveau Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) dans notre base de connaissances de support.
1. Si le problème semble temporaire, effectuez des étapes d’atténuation telles qu’une mise à niveau ou placez le site en mode de maintenance. Pour les étapes, reportez-vous à la section [Comment demander le redimensionnement temporaire](/help/how-to/general/how-to-request-temporary-magento-upsize.md) dans notre base de connaissances de support et au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs. Si la mise à niveau renvoie le site à des opérations normales, pensez à demander une mise à niveau permanente (contactez votre équipe de compte d’Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes ou le code qui réduit la pression sur les services. Pour les étapes, reportez-vous à la section [Déploiement de test > Chargement et test de stress](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) de notre documentation destinée aux développeurs sur l’infrastructure cloud d’Adobe Commerce.
