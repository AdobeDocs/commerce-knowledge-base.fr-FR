---
title: "Alertes gérées pour Adobe Commerce : alerte d’avertissement du processeur"
description: Cet article décrit les étapes de dépannage lorsque vous recevez une alerte d’avertissement du processeur pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce : alerte d’avertissement du processeur

Cet article décrit les étapes de dépannage lorsque vous recevez une alerte d’avertissement du processeur pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![Alerte d’avertissement du processeur](assets/cpu-warning-magento-managed.png){width="500"}

## Produits et versions concernés

Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro

## Problème

Vous recevrez une alerte dans New Relic si vous avez signé jusqu’à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux clients un ensemble standard utilisant les informations du service d’assistance et d’ingénierie.

<u> **Do!** </u>

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site ne répond pas complètement. Pour les étapes, reportez-vous au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour les étapes, reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u>**Ne pas faire !**</u>

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire l’administration de Commerce, les importations/exportations de données).
* Effacez le cache.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

1. Utilisez la [page des transactions de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :
   * Triez les transactions par scores Apdex croissants. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. [Un score Apdex faible](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Il s’agit généralement de la base de données, de Redis ou de PHP. Pour connaître les étapes, reportez-vous à la section New Relic [Affichage des transactions présentant le plus grand insatisfaction Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions selon le débit le plus élevé, le temps de réponse moyen le plus lent, le plus long et d’autres seuils. Pour les étapes, reportez-vous à la section New Relic [Trouver des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si vous avez encore du mal à identifier la source, utilisez la [page d&#39;infrastructure du New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) pour identifier les services lourds de ressources. Pour les étapes, reportez-vous à la section New Relic [Page Hôtes de surveillance de l’infrastructure > Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si vous identifiez la source, connectez-vous à l’environnement pour en savoir plus. Pour les étapes, reportez-vous à la section [Cloud pour Adobe Commerce > SSH dans votre environnement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) de notre documentation destinée aux développeurs.
1. Si vous avez toujours du mal à identifier la source :
   * Examinez les tendances récentes pour identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
   * Pensez à rechercher et désactiver des catalogues plats. Pour les étapes, reportez-vous à la section [Cons lents, lents et à exécution longue](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) de notre base de connaissances de support.
   * Si vous pensez que vous rencontrez une attaque DDoS, essayez de bloquer le trafic de robots. Pour les étapes, reportez-vous à la section [Comment bloquer le trafic malveillant pour Adobe Commerce à un niveau Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) dans notre base de connaissances de prise en charge.
1. Si le problème semble temporaire, effectuez des étapes d’atténuation telles qu’une mise à niveau ou placez le site en mode de maintenance. Pour les étapes, reportez-vous à la section [Comment demander le redimensionnement temporaire](/help/how-to/general/how-to-request-temporary-magento-upsize.md) dans notre base de connaissances de support, et au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs. Si la mise à niveau renvoie le site à des opérations normales, pensez à demander une mise à niveau permanente (contactez votre équipe de compte d’Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes, ou du code qui réduit la pression sur les services. Pour les étapes, reportez-vous à la section [Cloud pour Adobe Commerce > Déploiement de tests > Chargement et test de stress](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) dans notre documentation destinée aux développeurs.
