---
title: Elasticsearch dans le dépannage d’Adobe Commerce
description: Les problèmes Elasticsearch sur Adobe Commerce peuvent être résolus à l’aide de l’outil de dépannage Elasticsearch. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch dans le dépannage d’Adobe Commerce

Les problèmes Elasticsearch sur Adobe Commerce peuvent être résolus à l’aide de l’outil de dépannage Elasticsearch. Cliquez sur chaque question pour afficher la réponse à chaque étape de l’outil de dépannage.

>[!WARNING]
>
>Sur Adobe Commerce sur l’infrastructure cloud, notez que les mises à niveau de service ne peuvent pas être transférées vers l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production. 48 heures avant que vos modifications ne soient en production [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle le processus de mise à niveau doit commencer.

## Étape 1 - Rechercher un problème d’Elasticsearch {#step-1}

+++**Votre problème peut-il être lié à un Elasticsearch ?**

Problèmes Elasticsearch indiqués par les messages d’erreur, &quot;_Aucun noeud vivant trouvé dans votre grappe&quot;,_ les produits manquants et l’affichage d’anciennes informations sur les produits.

a. OUI - Passez à [Étape 2](#step-2).\
b. NO - Recherchez à nouveau les termes de recherche pertinents dans la variable [Base de connaissances du centre d’aide Adobe Commerce](https://support.magento.com/hc).

+++

## Étape 2 - Vérification du problème d’installation {#step-2}

+++**S’agit-il d’une nouvelle installation d’Elasticsearch ?**

a. OUI - [Assurez-vous que Elasticsearch est installé correctement.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Vérifiez également si vous utilisez Adobe Commerce sur l’infrastructure cloud 2.3.1 ou version ultérieure. Les commerçants qui ont effectué une mise à niveau vers Adobe Commerce sur l’infrastructure cloud (versions 2.3.1 et ultérieures) et qui utilisent une version d’Elasticsearch antérieure à la version 6.x peuvent rencontrer des erreurs lors du déploiement. Pour résoudre ce problème, le module client Elasticsearch et le service Elasticsearch doivent se trouver sur les dernières versions recommandées. Pour les étapes, voir [Problèmes d’Elasticsearch après la mise à niveau vers Adobe Commerce on cloud infrastructure 2.3.1+](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NO - Vérifiez l’intégrité de votre grappe. Si vous utilisez un environnement d’évaluation ou de production Pro, exécutez la commande suivante : `curl -m1 localhost:9200/_cluster/health?pretty`. Si vous utilisez un environnement d’intégration (qui comprend toutes les branches de démarrage), exécutez `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Passez à [Étape 3](#step-3).

+++

## Étape 3 - Vérification de la disponibilité de la grappe Elasticsearch {#step-3}

+++**Avez-vous reçu une réponse du service ?**

a. OUI - Passez à [Étape 4](#step-4).\
b. NO - Passez à [Étape 9](#step-9).

+++

## Étape 4 - Vérification de l’intégrité du cluster Elasticsearch {#step-4}

+++**Réponse verte ?**

a. OUI : l’Elasticsearch est disponible pour le traitement des données et la réindexation devrait fonctionner. Passez à [Étape 5](#step-5).\
b. NON - Jaune ou rouge signifie qu’il existe des problèmes de connexion entre les noeuds, et certaines données peuvent ne pas être disponibles. En jaune, exécutez la commande : `php bin/magento config:show catalog/search/engine` pour vérifier votre moteur de recherche. Passez à [Étape 6](#step-6). Si rouge, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 5 - Vérification du fonctionnement de la recherche {#step-5}

+++**Problème de recherche ?**

Les symptômes peuvent inclure l’absence de produits, des catégories vides ou aucune mise à jour de produits ou de catégories de produits n’est correcte.

a. OUI - Exécutez cette commande pour vérifier l’état de la recherche catalogue : `php bin/magento indexer:status`. Passez à [Étape 8](#step-8).\
b. NO - Exécutez la commande : `php bin/magento config:show catalog/search/engine`. Passez à [Étape 6](#step-6).

+++

## Étape 6 - Vérifier ElasticSuite {#step-6}

+++**ElasticSuite en cours d’utilisation ?**

a. OUI - Vérifiez si ElasticSuite se trouve dans la version actuelle en exécutant cette commande : `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Pour vérifier si cette version est dépréciée ou recommandée, voir [Github : Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Si ElasticSuite est à jour, passez à [Étape 10](#step-10).\
b. NON - passez à [Étape 7](#step-7).

+++

## Etape 7 - Vérification de la mise à jour des outils de la CEE {#step-7}

+++**Est-ce que les outils ETC sont la dernière version ?**

Exécutez la commande : `php ./vendor/bin/ece-tools -V` et vérifiez la version des outils ECE. S’agit-il de la variable [dernière version des outils de la CEE](https://github.com/magento/ece-tools/releases)?

a. OUI - Passez à [Étape 5a](#step-5).\
b. NO - Mettez à niveau les outils de la CEE vers la version la plus récente. Exécutez la commande `php bin/magento config: show catalog/search/engine` pour vérifier votre moteur de recherche. Passez à [Étape 6](#step-6).

+++

## Etape 8 - Vérifier la réindexation {#step-8}

+++**L’état de recherche catalogue dans _Traitement_?**

a. OUI - Vous devez attendre que le traitement soit terminé, puis vérifier si les catégories de produits ont été mises à jour. Dans le cas contraire, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Si l’état de la recherche catalogue est _Réindexation requise_ Exécutez dans CLI/Terminal : `php bin/magento cron:run`. Si cela ne fonctionne pas, exécutez : `php bin/magento indexer:reindex`. Si cela ne résout pas le problème, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etape 9 - Vérification de la configuration du yaml {#step-9}

+++**`.yaml`fichier récemment mis à jour ?**

a. OUI - Vérifier `.yaml` Configuration des Elasticsearch en faisant référence à DevDocs [Configuration de l’Elasticsearch : pour activer l’Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etape 10 - Recherche des index de tracking {#step-10}

+++**Existe-t-il des indices de tracking dans la liste ?**

Exécuter `curl elasticsearch.internal:9200/_cat/indices` (si vous vous trouvez dans un environnement d’intégration qui comprend toutes les branches de Starter). Si vous vous trouvez dans un environnement d’évaluation ou de production Pro `curl localhost:9200/_cat/indices`. Existe-t-il des indices de tracking dans la liste ? Vérifiez la sortie pour`_tracking_log_`.

a. OUI - Si vous utilisez une version d’ElasticSuite antérieure à la version 2.8.0, il est recommandé de [mise à niveau vers Elastic Suite 2.8.0 pour ajuster la rétention des index de suivi ou désactiver le suivi](https://support.magento.com/hc/en-us/articles/360035266131?). Si vous ne pouvez pas effectuer immédiatement la mise à niveau, vous pouvez [créer un cron pour supprimer les index de suivi ;](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Cela peut toutefois entraîner des problèmes de performances. Une fois que vous avez effectué la mise à niveau vers ElasticSuite 2.8.0 ou supprimé les index de suivi, exécutez la commande (si vous utilisez des environnements d’évaluation ou de production Pro) :`localhost:9200/_cat/allocation?v` pour vérifier l’espace disponible. Si vous utilisez l’un des environnements d’intégration (qui inclut toutes les branches de Starter), exécutez `elasticsearch.internal:9200/_cat/allocation?v`. Passez à [Étape 11](#step-11).\
b. NO : si vous utilisez des environnements d’évaluation ou de production Pro, exécutez-les. `localhost:9200/_cat/allocation?v` et vérifiez l’espace disponible. Si vous utilisez l’un des environnements d’intégration (qui inclut toutes les branches de Starter), exécutez `elasticsearch.internal:9200/_cat/allocation?v`. Passez à [Étape 11](#step-11).

+++

## Étape 11 - Recherche d’une erreur spécifique {#step-11}

+++**Erreur spécifique ?**

Journaux Adobe Commerce et ES, extensions et code personnalisé.

a. OUI - Consultez l’article Résolution des problèmes du centre d’aide Adobe Commerce [Assurez-vous que l’Elasticsearch est correctement installé](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) ou [Elasticsearch se bloque ou rencontre des problèmes de mémoire lors de l’utilisation du module externe ElasticSuite](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NO - Passez à [Étape 12](#step-12).

+++

## Étape 12 - Vérifier le stockage disponible {#step-12}

+++**Utilisation du stockage > 85 % ?**

a. OUI - Vous devez augmenter le stockage disponible. Reportez-vous à DevDocs .[Configuration de l’Elasticsearch : pour activer l’Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). Exécutez ensuite : `localhost:9200/_cat/allocation?v` (si vous utilisez des environnements d’évaluation ou de production Pro). Si vous utilisez l’un des environnements d’intégration (qui comprend toutes les branches de démarrage), exécutez : `elasticsearch.internal:9200/_cat/allocation?v`. Passez à [Étape 11](#step-11).\
b. NON - [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Retour à l’étape 1](#step-1)
