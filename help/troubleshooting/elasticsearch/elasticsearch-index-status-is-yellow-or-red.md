---
title: 'Statut de l’index Elasticsearch : "jaune" ou "rouge"'
description: L’article fournit un correctif lorsque l’état de l’index Elasticsearch n’est pas "*vert*". '*jaune*' indique normal, et '*rouge*' indique mauvais. L’état "jaune" ou "rouge" peut survenir conjointement avec les produits manquants ou l’affichage d’anciennes informations sur les produits.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Statut de l’index Elasticsearch : &quot;jaune&quot; ou &quot;rouge&quot;

>[!WARNING]
>
> [Le moteur de recherche de catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Vous devez avoir configuré et configuré l’hôte Elasticsearch avant d’installer la version 2.4.0. Voir [Installation et configuration de l’Elasticsearch](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/overview-search).

L’article fournit un correctif lorsque l’état de l’index Elasticsearch n’est pas &quot;*vert*&quot;. &#39;*jaune*&#39; indique normal et &#39;*rouge*&#39; indique mauvais. L’état &quot;jaune&quot; ou &quot;rouge&quot; peut survenir conjointement avec les produits manquants ou l’affichage d’anciennes informations sur les produits.

## Versions et produits concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problème

L’index de recherche de catalogue Elasticsearch est lent, ce qui entraîne un état de &#39;*jaune*&#39; ou &#39;*rouge*&#39; au lieu de &#39;*vert*&#39;. Vous pouvez également rencontrer des modifications manquantes sur le front-end.

## Cause

Il peut y avoir plusieurs causes potentielles. L’une des causes est que l’instance Elasticsearch manque d’espace disque. Les indices dupliqués sont une autre cause.

## Solution

Créez un nouveau vidage mysql avant de suivre ces étapes et effectuez-les en dehors des heures de bureau afin d’éviter toute incidence potentielle sur vos clients :

1. Basculez temporairement vers la recherche MySQL - activez la recherche MySQL. (Remarque : N’oubliez pas de revenir à l’Elasticsearch ou vous pouvez rencontrer des problèmes de performances).
1. Pour identifier les index dupliqués, exécutez la commande suivante :

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. Pour supprimer des index :

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Réactivez Elasticsearch.
1. Exécutez la réindexation complète.
1. Vérifiez l’état des index en exécutant la commande suivante :

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Si ces étapes ne fonctionnent pas, [soumettez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lecture connexe

Pour en savoir plus, reportez-vous à la section [API Elasticsearch Cluster health](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
