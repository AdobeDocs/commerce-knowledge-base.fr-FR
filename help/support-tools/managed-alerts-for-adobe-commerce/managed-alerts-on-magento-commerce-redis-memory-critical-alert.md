---
title: "Alertes gérées sur Adobe Commerce : alerte critique de mémoire de révision"
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte critique de mémoire Redis pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : permet de réduire l’alerte critique de mémoire

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte critique de mémoire Redis pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné.

![new_relic_redis_memory_critical.png](assets/new_relic_redis_memory_critical.png)

## Produits et versions concernés

Toutes les versions d’Adobe Commerce sur l’architecture de plan de l’infrastructure cloud Pro

## Problème

Vous recevrez une alerte dans New Relic si vous avez signé jusqu’à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux commerçants un ensemble standard d’alertes à l’aide d’informations provenant de l’assistance et de l’ingénierie.

**<u>Do!</u>**

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour les étapes, reportez-vous au [Guide d&#39;installation > Activer ou désactiver le mode de maintenance](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) de notre Guide d&#39;installation. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour les étapes, reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) de notre Guide d&#39;installation.

**<u>Ne pas faire !</u>**

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire une action majeure dans l’administrateur de Commerce, comme l’importation/exportation de données, le vidage de médias, l’enregistrement de catégories avec un grand nombre de produits attribués et les mises à jour en masse).
* Effacez le cache.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

**Puisqu&#39;il s&#39;agit d&#39;une alerte critique, il est vivement recommandé de terminer l&#39;étape 1 avant de tenter de résoudre le problème (à partir de l&#39;étape 2).**

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes, reportez-vous à la section [Suivi de vos tickets d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances d&#39;assistance. L’assistance a peut-être déjà reçu une alerte de seuil New Relic, créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit comporter les informations suivantes :

   * Raison de contact : sélectionnez &quot;New Relic CRITICAL alert received&quot;.
   * Description de l’alerte.
   * [Lien d’incident New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Elle est incluse dans vos [alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. S’il n’existe aucun ticket de support, vérifiez si Redis Used Memory augmente ou diminue en accédant à la page [one.newrelic.com](https://login.newrelic.com) > **Infrastructure** > **Services tiers** , puis sélectionnez le tableau de bord Redis . S&#39;il est stable ou en augmentation, [envoyez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour que votre grappe soit mise à niveau ou augmentez la limite `maxmemory` au niveau suivant.
1. Si vous ne pouvez pas identifier la cause de l’augmentation de la consommation de mémoire Redis, passez en revue les tendances récentes afin d’identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
1. Vérifiez si les extensions tierces ne se comportent pas correctement :

   * Essayez de trouver une corrélation avec les extensions tierces récemment installées et l’heure à laquelle le problème a commencé.
   * Examinez les extensions qui pourraient affecter le cache Adobe Commerce et entraîner une croissance rapide du cache. Par exemple, des blocs de mise en page personnalisés, le remplacement de la fonctionnalité de cache et le stockage de grandes quantités de données dans le cache.

1. S’il n’existe aucune preuve de comportement incorrect des extensions, [installez les derniers correctifs pour corriger les problèmes Redis pour Adobe Commerce sur l’infrastructure cloud](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. Si les étapes ci-dessus ne vous aident pas à identifier ou à résoudre le problème, envisagez d’activer le cache L2 pour réduire le trafic réseau entre l’application et Redis. Pour des informations générales sur ce qu&#39;est le cache L2, reportez-vous à la section [Mise en cache L2 dans l&#39;application Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) de notre documentation destinée aux développeurs. Pour activer le cache L2 pour l’infrastructure cloud, essayez les méthodes suivantes :

   * Mettez à niveau les outils de la CEE sous la version 2002.1.2.
   * Configurez le cache L2 en utilisant [Use REDIS\_BACKEND variable](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) et en mettant à jour le fichier `.magento.env.yaml` :

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
