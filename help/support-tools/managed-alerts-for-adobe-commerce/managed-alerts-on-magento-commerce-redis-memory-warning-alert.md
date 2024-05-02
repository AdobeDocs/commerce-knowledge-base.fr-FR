---
title: "Alertes gérées sur Adobe Commerce : alerte d’avertissement de mémoire de révision"
description: "Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte d’avertissement Redis pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte ressemblera à ce qui suit, selon le canal de notification d’alerte sélectionné :"
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alerte d’avertissement de mémoire réduite

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte d’avertissement Redis pour Adobe Commerce dans New Relic. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte sélectionné :

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Produits et versions concernés

Toutes les versions d’Adobe Commerce sur l’infrastructure cloud Pro planifient l’architecture.

## Problème

Vous recevrez une alerte dans New Relic si vous vous êtes abonné à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux commerçants un ensemble standard d’alertes à l’aide d’informations provenant de l’assistance et de l’ingénierie.

**<u>Faites-le !</u>**

* Il est recommandé d’abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Si votre site est ou ne répond plus complètement, mettez immédiatement votre site en mode de maintenance. Pour connaître les étapes, voir [Guide d’installation > Activer ou désactiver le mode de maintenance](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) dans notre Guide d’installation.
* Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour connaître les étapes, voir [Maintenir la liste des adresses IP exemptées](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) dans notre Guide d’installation.

**<u>Ne le faites pas !</u>**

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur le processeur ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire une action majeure dans l’administrateur de Commerce, comme l’importation/exportation de données, le vidage de médias, l’enregistrement de catégories avec un grand nombre de produits attribués et les mises à jour en masse).
* Effacez le cache.

## Solution

Suivez ces étapes pour identifier et dépanner la cause.

1. Vérifiez si la mémoire utilisée Redis augmente ou diminue en accédant à [one.newrelic.com](https://login.newrelic.com/login) > **Infrastructure** > **Services tiers** , sélectionnez le tableau de bord Redis . S’il est stable ou en augmentation, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour que votre grappe soit mise à niveau ou augmentez les `maxmemory` limite au niveau suivant.
1. Si vous ne pouvez pas identifier la cause de l’augmentation de la consommation de mémoire Redis, passez en revue les tendances récentes afin d’identifier les problèmes liés aux déploiements de code récents ou aux modifications de configuration (par exemple, de nouveaux groupes de clients et des modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toute corrélation dans les déploiements ou modifications de code.
1. Vérifiez si les extensions tierces ne se comportent pas correctement :
   * Essayez de trouver une corrélation avec les extensions tierces récemment installées et l’heure à laquelle le problème a commencé.
   * Examinez les extensions qui pourraient affecter le cache Adobe Commerce et entraîner une croissance rapide du cache. Par exemple, des blocs de mise en page personnalisés, le remplacement de la fonctionnalité de cache et le stockage de grandes quantités de données dans le cache.
1. S’il n’existe aucune preuve de comportement inapproprié des extensions, [Installez les derniers correctifs pour résoudre les problèmes Redis pour Adobe Commerce sur l’infrastructure cloud](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md). Si les étapes ci-dessus ne vous aident pas à identifier ou à résoudre le problème, envisagez d’activer le cache L2 pour réduire le trafic réseau entre l’application et Redis. Pour des informations générales sur ce qui est du cache L2, reportez-vous à la section [Mise en cache de l2 dans l’application Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) dans notre Guide de configuration. Pour activer le cache L2 pour l’infrastructure cloud, essayez les méthodes suivantes :
   * Mettez à niveau les outils de la CEE sous la version 2002.1.2.
   * Configuration du cache L2 à l’aide de [Utiliser la variable REDIS\_BACKEND](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) et mise à jour `.magento.env.yaml` fichier :

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
