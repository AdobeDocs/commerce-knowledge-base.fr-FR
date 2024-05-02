---
title: Problèmes Elasticsearch après la mise à niveau de l’infrastructure cloud Adobe Commerce 2.3.1+
description: Cet article décrit un correctif pour les problèmes survenant lors du déploiement après la mise à niveau vers Adobe Commerce sur les versions 2.3.1+ de l’infrastructure cloud, si vous utilisez les versions 2.x et 5.x de l’Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problèmes Elasticsearch après la mise à niveau de l’infrastructure cloud Adobe Commerce 2.3.1+

>[!WARNING]
>
>[Le moteur de recherche de catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Vous devez avoir configuré et configuré l’hôte Elasticsearch avant d’installer la version 2.4.0. Voir [Installation et configuration de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Veuillez noter que les mises à niveau de service ne peuvent pas être transmises à l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production. 48 heures avant que vos modifications ne soient en production [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle le processus de mise à niveau doit commencer.

Cet article décrit un correctif pour les problèmes survenant lors du déploiement après la mise à niveau vers Adobe Commerce sur les versions 2.3.1+ de l’infrastructure cloud, si vous utilisez les versions 2.x et 5.x de l’Elasticsearch.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.3.1+
* Elasticsearch 2.x et 5.x

## Cause

Les commerçants qui ont effectué une mise à niveau vers Adobe Commerce sur l’infrastructure cloud (versions 2.3.1 et ultérieures) et qui utilisent une version d’Elasticsearch antérieure à la version 6.x peuvent rencontrer des erreurs lors du déploiement. En effet, les versions 2.x et 5.x des Elasticsearch sont [Fin de vie](https://www.elastic.co/support/eol) et ne sont plus pris en charge dans Adobe Commerce. Le client Elasticsearch doit être à jour, sinon l’exécution d’un déploiement risque de déclencher une erreur. Pour en savoir plus, voir [Modification du client Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) dans notre documentation destinée aux développeurs.

## Problème

Lors du déploiement, un message d’erreur similaire au suivant s’affiche, indiquant que la version de votre Elasticsearch n’est pas compatible : *Le service Elasticsearch version 5.2.2 sur la couche d’infrastructure n’est pas compatible avec la version actuelle du module élasticsearch/élasticsearch (6.7.0.0), utilisé par votre application Magento.*  *Vous pouvez résoudre ce problème en mettant à niveau le service Elasticsearch de votre infrastructure cloud Magento vers la version 6.x.*. D’autres symptômes de ce problème peuvent être l’absence d’images et de problèmes liés aux filtres dans votre environnement.

## Solution

>[!WARNING]
>
>Si vous disposez d’un environnement partagé, vérifiez que l’évaluation et la production sont prêtes à être mises à niveau.

Pour résoudre ce problème, le module client Elasticsearch et le service Elasticsearch doivent se trouver sur les dernières versions recommandées :

1. Suivez les instructions de la section [modifier le module Elasticsearch ;](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) dans notre documentation destinée aux développeurs afin que vous ayez la dernière version recommandée du module client Elasticsearch.
1. [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et demander une mise à jour du service Elasticsearch vers la version 6.x lors de l’évaluation et de la production. Veuillez noter qu’une mise à niveau vers le service Elasticsearch peut prendre du temps.

## Lecture connexe

* [Exigences en matière de pile de technologie Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) dans notre documentation destinée aux développeurs.
* [Configuration du service Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) dans notre documentation destinée aux développeurs.
* [Installation et configuration de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) dans notre documentation destinée aux développeurs.
* [Assurez-vous que l’Elasticsearch est correctement installé](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) dans notre base de connaissances de soutien.
