---
title: "Alertes gérées pour Adobe Commerce : alerte critique Apdex"
description: Cet article décrit les étapes de dépannage lorsque vous recevez une alerte Apdex critique pour Adobe Commerce dans New Relic. Le score Apdex mesure la satisfaction des utilisateurs quant au temps de réponse des applications et services web. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: fbb24fb3c8b399f3b7e19c663eb4b168657498e6
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce : alerte critique Apdex

Cet article décrit les étapes de dépannage lorsque vous recevez une alerte Apdex critique pour Adobe Commerce dans New Relic. Le score Apdex mesure la satisfaction des utilisateurs quant au temps de réponse des applications et services web. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![alerte critique apdex](assets/apdex-critical-magento-managed.png){width="500"}

## Produits et versions concernés

* Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro
* Architecture du plan de démarrage d’Adobe Commerce sur l’infrastructure cloud

## Problème

Vous recevrez une alerte gérée dans New Relic si vous avez signé jusqu’à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux commerçants un ensemble standard d’informations provenant du support et de l’ingénierie.

<u> **Do!** </u>

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour les étapes, reportez-vous au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour les étapes, reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u>**Ne pas faire !**</u>

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez les tâches administratives principales (c’est-à-dire l’administrateur Commerce, les imports/exports de données).
* Effacez le cache.

En procédant comme suit lorsque vous avez reçu une alerte critique, avant de résoudre les problèmes liés à la cause de l’alerte, votre site risque de ne plus être réactif si vous n’êtes pas déjà en panne.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

>[!WARNING]
>
>Puisqu’il s’agit d’une alerte critique, il est vivement recommandé de terminer l’**étape 1** avant de tenter de résoudre le problème (à partir de l’étape 2).

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes, reportez-vous à la section [Suivi de vos tickets d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances d&#39;assistance. L’assistance a peut-être reçu une alerte de seuil New Relic, créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit comporter les informations suivantes :
   * Raison de contact : sélectionnez &quot;New Relic CRITICAL alert received&quot;.
   * Description de l’alerte.
   * [Lien d’incident New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Elle est incluse dans vos [alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Pour identifier la source du problème, utilisez la [page des transactions de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :
   * Triez les transactions par scores Apdex croissants. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. Un score Apdex faible peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Il s’agit généralement de la base de données, de Redis ou de PHP. Pour connaître les étapes, reportez-vous à la section New Relic [Affichage des transactions présentant le plus grand insatisfaction Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Triez les transactions selon le débit le plus élevé, le temps de réponse moyen le plus lent, le plus long et d’autres seuils. Pour les étapes, reportez-vous à la section New Relic [Trouver des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si vous avez encore du mal à identifier le problème, utilisez la page Infrastructure de New Relic APM.
1. Utilisez la [page d’infrastructure de New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) pour identifier les processus gourmands en ressources. Pour les étapes, reportez-vous à la section New Relic [Page Hôtes de surveillance de l’infrastructure > Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si des services tels que Redis ou MySQL sont la principale source de consommation de mémoire, essayez les méthodes suivantes :
   * Vérifiez que vous utilisez la dernière version. Les versions plus récentes peuvent parfois corriger les fuites de mémoire. Si vous n’utilisez pas la dernière version, envisagez de mettre à niveau. Pour les étapes, reportez-vous à [Cloud pour Adobe Commerce > Services > Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) dans notre documentation destinée aux développeurs.
   * Recherchez des problèmes MySQL tels que des requêtes longues, des clés de Principal non définies et des index en double. Pour obtenir les étapes nécessaires, reportez-vous à la section [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) de notre documentation destinée aux développeurs.
   * Recherchez des problèmes PHP. Vérifiez les processus en cours d’exécution en exécutant `ps aufx` dans l’interface de ligne de commande/le terminal. Dans la sortie du terminal, vous verrez les traitements et processus cron en cours d’exécution. Vérifiez la sortie pour le temps d&#39;exécution des processus. S’il existe un cron avec un long délai d’exécution, le cron peut être suspendu. Pour obtenir des instructions de dépannage, reportez-vous aux sections [Tâche lente, lente et longue exécution des crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) et [Tâche Cron bloquée dans l’état &quot;en cours d’exécution&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) dans notre base de connaissances de support.

1. Une fois la source identifiée, connectez-vous à l&#39;environnement pour en savoir plus. Pour les étapes, reportez-vous à [Cloud pour Adobe Commerce > Technologies et exigences > SSH dans votre environnement](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) dans notre documentation destinée aux développeurs.
1. Si vous avez toujours du mal à identifier la source, passez en revue les tendances récentes afin d’identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
1. Si vous ne parvenez pas à trouver une solution dans un délai raisonnable, demandez une mise à niveau ou mettez un site en mode de maintenance si vous ne l’avez pas déjà fait. Pour les étapes, reportez-vous à la section [Comment demander le redimensionnement temporaire](/help/how-to/general/how-to-request-temporary-magento-upsize.md) dans notre base de connaissances de support, et au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs.
1. Si la mise à niveau renvoie le site à des opérations normales, pensez à demander une mise à niveau permanente (contactez votre équipe de compte d’Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes, ou du code qui réduit la pression sur les services. Reportez-vous à la section [Cloud pour Adobe Commerce > Déploiement de tests > Chargement et test de stress](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) dans notre documentation destinée aux développeurs.
