---
title: "Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire"
description: Cet article décrit les étapes de dépannage pour lorsque vous recevez une alerte d’avertissement de mémoire pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire

Cet article décrit les étapes de dépannage pour lorsque vous recevez une alerte d’avertissement de mémoire pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![avertissement de mémoire](assets/memory-warning-magento-managed.png){width="500"}

## Produits et versions concernés

Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro

## Problème

Vous recevrez une alerte dans New Relic si vous avez signé jusqu’à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe Commerce pour fournir aux clients un ensemble standard d’informations provenant de l’assistance et de l’ingénierie.

<u>**Do!**</u> :

* Il est recommandé d’abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour les étapes, reportez-vous au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour les étapes, reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u>**Don&#39;t !**</u> :

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire l’administrateur, les imports/exports de données).
* Effacez le cache.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

1. Utilisez la [page d’infrastructure de New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) pour identifier les processus gourmands en mémoire. Pour les étapes, reportez-vous à la section New Relic [Page Hôtes de surveillance de l’infrastructure > Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Si des services tels que Redis ou MySQL sont la principale source de consommation de mémoire, essayez les méthodes suivantes :

   * Vérifiez que vous utilisez la dernière version. Les versions plus récentes peuvent parfois corriger les fuites de mémoire. Si vous n’utilisez pas la dernière version, envisagez de mettre à niveau. Pour les étapes, reportez-vous à [Adobe Commerce on cloud infrastructure > Services > Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) dans notre documentation destinée aux développeurs.
   * Si vous ne parvenez toujours pas à identifier la source de l’augmentation de la consommation de mémoire, recherchez des problèmes MySQL tels que les requêtes longues, les clés de Principal non définies et les index en double. Pour les étapes, reportez-vous à la section [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) dans notre base de connaissances de prise en charge.
   * S’il n’y a aucun problème MySQL, recherchez les problèmes PHP. Vérifiez les processus en cours d’exécution en exécutant `ps aufx` dans l’interface de ligne de commande/le terminal. Dans la sortie du terminal, vous verrez les traitements et processus cron en cours d’exécution. Vérifiez la sortie pour le temps d&#39;exécution des processus. S’il existe un cron avec un long délai d’exécution, le cron peut être suspendu. Pour connaître les étapes de dépannage, reportez-vous aux sections [Tâche lente, lente et longue exécution des crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) et [Tâche Cron bloquée dans l’état &quot;en cours d’exécution&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) dans notre base de connaissances de support.

1. Si vous avez toujours du mal à identifier la source du problème, utilisez la [page des transactions de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :

   * Triez les transactions par scores Apdex croissants. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. Un [score Apdex faible](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Il s’agit généralement de la base de données, Redis ou PHP. Pour connaître les étapes, reportez-vous à la section New Relic [Affichage des transactions présentant le plus grand insatisfaction Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions selon le débit le plus élevé, le temps de réponse moyen le plus lent, le plus long et d’autres seuils. Pour les étapes, reportez-vous à la section New Relic [Trouver des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si vous avez encore du mal à identifier le problème, utilisez la page Infrastructure de New Relic APM.

1. Si vous ne pouvez pas identifier la cause de l’augmentation de la consommation de mémoire, passez en revue les tendances récentes afin d’identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.

1. Si les méthodes ci-dessus ne vous aident pas à trouver la cause et/ou la solution dans un délai raisonnable, demandez une mise à niveau ou mettez le site en mode de maintenance si ce n’est déjà fait. Pour les étapes, reportez-vous à la section [Comment demander le redimensionnement temporaire](/help/how-to/general/how-to-request-temporary-magento-upsize.md) dans notre base de connaissances de support et au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs.

1. Si la mise à niveau renvoie le site à des opérations normales, pensez à demander une mise à niveau permanente (contactez votre équipe de compte d’Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes, ou du code qui réduit la pression sur les services. Reportez-vous à la section [Adobe Commerce on cloud infrastructure > Test de déploiement > Chargement et test de stress](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) dans notre documentation destinée aux développeurs.
