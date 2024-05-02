---
title: "Alertes gérées sur Adobe Commerce : alerte critique du processeur"
description: Cet article décrit les étapes de dépannage lorsque vous recevez une alerte critique du processeur pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 5be8f2969426078bfcc0e4ffb4895dcf0327165f
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alerte critique du processeur

Cet article décrit les étapes de dépannage lorsque vous recevez une alerte critique du processeur pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![alerte critique de disque](assets/cpu-critical-magento-managed.png){width="500"}

## Produits et versions concernés

Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro

## Problème

Vous recevrez une alerte gérée dans New Relic si vous vous êtes inscrit à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe Commerce pour fournir aux clients un ensemble standard d’informations provenant de l’assistance et de l’ingénierie.

<u>**Faites-le !**</u>:

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour connaître les étapes, voir [Guide d’installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour connaître les étapes, voir [Maintenir la liste des adresses IP exemptées](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) dans notre documentation destinée aux développeurs.

<u>**Ne le faites pas !**</u>:

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez les tâches administratives principales (c’est-à-dire l’administrateur Commerce, les imports/exports de données).
* Effacez le cache.

Votre site peut ne plus être réactif (si vous n’êtes pas déjà en panne) si vous effectuez l’une des actions &quot;Ne pas&quot; avant d’avoir enquêté et résolu la cause de l’alerte.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

>[!WARNING]
>
>Puisqu’il s’agit d’une alerte critique, il est vivement recommandé d’effectuer les opérations suivantes : **Étape 1** avant d’essayer de résoudre le problème (à partir de l’étape 2).

Vérifiez si le ticket d’assistance Adobe Commerce existe. Pour connaître les étapes, voir [Suivi des tickets d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances de soutien. La prise en charge a peut-être reçu une alerte de seuil New Relic, créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit comporter les informations suivantes :

1. Raison de contact : sélectionnez &quot;New Relic CRITICAL alert received&quot;.
1. Description de l’alerte.
1. [Lien d’incident New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Elle est incluse dans votre [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Utilisation [Page Transaction de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :
   * Triez les transactions par scores Apdex croissants. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs par rapport au temps de réponse de vos applications et services web. A [note basse d’Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Il est généralement lié à la base de données, Redis ou PHP. Pour connaître les étapes, voir New Relic [Afficher les transactions présentant le plus grand insatisfaction Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions selon le débit le plus élevé, le temps de réponse moyen le plus lent, le plus long et d’autres seuils. Pour connaître les étapes, voir New Relic [Trouver des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si vous avez encore des difficultés à identifier la source, utilisez [Page d’infrastructure du New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) pour identifier les services lourds en ressources. Pour connaître les étapes, voir New Relic [Page Hôtes de surveillance de l’infrastructure > Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si vous identifiez la source, connectez-vous à l’environnement pour en savoir plus. Pour connaître les étapes, voir [SSH dans votre environnement pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) dans notre documentation destinée aux développeurs.
1. Si vous avez toujours du mal à identifier la source :
   * Examinez les tendances récentes pour identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
   * Pensez à rechercher et désactiver des catalogues plats. Pour connaître les étapes, voir [Lenteur des performances, lenteur et longueur des fils](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) dans notre base de connaissances de soutien.
   * Si vous pensez que vous rencontrez une attaque DDoS, essayez de bloquer le trafic de robots. Pour connaître les étapes, voir [Comment bloquer le trafic malveillant pour Adobe Commerce sur l’infrastructure cloud à un niveau Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) dans notre base de connaissances de soutien.
1. Si le problème semble temporaire, effectuez des étapes d’atténuation telles qu’une mise à niveau ou placez le site en mode de maintenance. Pour connaître les étapes, voir [Comment demander le redimensionnement temporaire](/help/how-to/general/how-to-request-temporary-magento-upsize.md) dans notre base de connaissances de soutien; [Guide d’installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs. Si la mise à niveau renvoie le site à des opérations normales, pensez à demander une mise à niveau permanente (contactez votre équipe de compte d’Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes ou le code qui réduit la pression sur les services. Pour connaître les étapes, voir [Déploiement des tests > Tests de charge et tests de stress](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) dans notre documentation destinée aux développeurs pour Adobe Commerce sur l’infrastructure cloud.
