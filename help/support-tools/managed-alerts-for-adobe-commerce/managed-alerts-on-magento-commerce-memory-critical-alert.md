---
title: "Alertes gérées sur Adobe Commerce : alerte critique de mémoire"
description: Cet article décrit les étapes de dépannage lorsque vous recevez une alerte critique de mémoire pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 468ad1c47da3c299b8028726e79e25a4aa9489ea
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alerte critique de mémoire

Cet article décrit les étapes de dépannage lorsque vous recevez une alerte critique de mémoire pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![alerte critique de disque](assets/memory-critical-magento-managed.png){width="500"}

## Produits et versions concernés

Toutes les versions d’Adobe Commerce sur l’infrastructure cloud Pro planifient l’architecture.

## Problème

Vous recevrez une alerte gérée dans New Relic si vous vous êtes inscrit à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux clients un ensemble standard utilisant les informations du service d’assistance et d’ingénierie.

<u> **Faites-le !** </u>

* Abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour connaître les étapes, voir [Guide d’installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour connaître les étapes, voir [Maintenir la liste des adresses IP exemptées](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u>**Ne le faites pas !**</u>

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire l’administration de Commerce, les importations/exportations de données).
* Effacez le cache.

Votre site peut ne plus être réactif (si vous n’êtes pas déjà en panne) si vous effectuez l’une des actions &quot;Ne pas&quot; avant d’avoir enquêté et résolu la cause de l’alerte.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

>[!WARNING]
>
>Puisqu’il s’agit d’une alerte critique, il est vivement recommandé d’effectuer les opérations suivantes : **Étape 1** avant d’essayer de résoudre le problème (à partir de l’étape 2).

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes, voir [Suivi des tickets d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances de soutien. L’assistance a peut-être déjà reçu une alerte de seuil New Relic, créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit comporter les informations suivantes :
   * Raison de contact : sélectionnez &quot;New Relic CRITICAL alert receive&quot;
   * Description de l’alerte
   * [Lien d’incident New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Elle est incluse dans votre [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Utilisation [Page d’infrastructure du New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) pour identifier les processus gourmands en mémoire. Pour connaître les étapes, voir New Relic [Page Hôtes de surveillance de l’infrastructure > Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Si des services tels que Redis, MySQL ou PHP sont les principales sources de consommation de mémoire, essayez les méthodes suivantes :
1. Vérifiez que vous utilisez les dernières versions. Les versions plus récentes peuvent parfois corriger les fuites de mémoire. Si vous n’utilisez pas la dernière version, envisagez de mettre à niveau. Pour connaître les étapes, voir [Adobe Commerce sur l’infrastructure cloud > Services > Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) dans notre documentation destinée aux développeurs.
1. Si le problème avec le service n’est pas lié à la version, essayez ce qui suit :
1. **MySQL**: recherchez des problèmes tels que les requêtes longues, les clés de Principal non définies et les index en double. Pour connaître les étapes, voir [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) dans notre base de connaissances de soutien.
1. **Redis**: si Redis est une source majeure de consommation de mémoire, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: si PHP est une source majeure de consommation de mémoire, passez en revue les processus en cours d’exécution. `ps aufx` dans l’interface de ligne de commande/le terminal. Dans la sortie du terminal, vous verrez les traitements et processus cron en cours d’exécution. Vérifiez la sortie pour le temps d&#39;exécution des processus. S’il existe un cron avec un long délai d’exécution, le cron peut être suspendu. Pour connaître les étapes de dépannage, voir [Lenteur des performances, lenteur et longueur des fils](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) et [Tâche Cron bloquée en état &quot;en cours d’exécution&quot;](https://support.magento.com/hc/en-us/articles/360033099451) dans notre base de connaissances de soutien.
1. Si vous avez encore du mal à identifier la source du problème, utilisez [Page Transaction de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :
   * Triez les transactions par scores Apdex croissants. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs par rapport au temps de réponse de vos applications et services web. A [note basse d’Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Il s’agit généralement de la base de données, de Redis ou de PHP. Pour connaître les étapes, voir New Relic [Afficher les transactions présentant le plus grand insatisfaction Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions selon le débit le plus élevé, le temps de réponse moyen le plus lent, le plus long et d’autres seuils. Pour connaître les étapes, voir New Relic [Trouver des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si vous avez encore du mal à identifier le problème, utilisez la page Infrastructure de New Relic APM.
1. Si vous ne pouvez pas identifier la cause de l’augmentation de la consommation de mémoire, passez en revue les tendances récentes afin d’identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les 7 derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
1. Si les méthodes ci-dessus ne vous aident pas à trouver la cause et/ou la solution dans un délai raisonnable, demandez une mise à niveau ou mettez un site en mode de maintenance si ce n’est déjà fait. Pour connaître les étapes, voir [Comment demander le redimensionnement temporaire](/help/how-to/general/how-to-request-temporary-magento-upsize.md) dans notre base de connaissances de soutien; [Guide d’installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs.
1. Si la mise à niveau renvoie le site à des opérations normales, pensez à demander une mise à niveau permanente (contactez votre équipe de compte d’Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes, ou du code qui réduit la pression sur les services. Voir [Adobe Commerce sur l’infrastructure cloud > Déploiement de test > Chargement et test de stress](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) dans notre documentation destinée aux développeurs.
