---
title: Les index de tracking ElasticSuite provoquent des problèmes avec Elasticsearch
description: Cet article aborde le problème des problèmes de mémoire d’Elasticsearch causés par les index de tracking générés par le plug-in ElasticSuite.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%
---
# Les index de tracking ElasticSuite provoquent des problèmes avec Elasticsearch

>[!NOTE]
>
>ElasticSuite et ses applications affiliées sont des outils tiers actuellement non pris en charge par Adobe. Ce contenu est présenté uniquement à titre d’information et non comme une indication de ce qui est activé pour la couverture d’assistance.

Cet article aborde le problème des problèmes de mémoire d’Elasticsearch causés par les index de tracking générés par le plug-in ElasticSuite.

## Produits et versions concernés

Les versions d’ElasticSuite antérieures à la version 2.8.0 ne sont pas en mesure de nettoyer régulièrement les index de suivi.

Les versions d&#39;ElasticSuite antérieures à la version 2.9.8/2.10.7 stockent les indices de tracking dans des indices quotidiens, ce qui entraîne une augmentation du nombre d&#39;indices ouverts.

## Problème

Si le plug-in tiers ElasticSuite est installé, vous pouvez rencontrer des problèmes de mémoire Elasticsearch et le service Elasticsearch peut se bloquer en raison d’indices de suivi ElasticSuite. Les symptômes incluent :

* Elasticsearch se bloque sans erreur de mémoire.
* Lors de l’exécution d’une commande d’intégrité `curl -m1 localhost:9200/_cluster/health?pretty` ou `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (pour les comptes de démarrage), il y a des centaines ou des milliers de `unassigned_shards`
* Les performances d’Elasticsearch ou du site sont sévèrement dégradées.
* *« Aucun nœud actif trouvé dans votre cluster »* dans le déploiement Elasticsearch ou consignez les erreurs.
* *« Rejet de la mise à jour du mappage vers [&lt;\*>_tracking_ log_event_&lt;\*>]« * en erreur de déploiement ou de journal.

## Cause

ElasticSuite a une nouvelle fonctionnalité qui crée des index de tracking. Ces indices de tracking enregistrent les termes de recherche les plus utilisés, ceux qui génèrent le plus de chiffre d&#39;affaires et ceux qui mènent à une page sans résultats afin que les commerçants puissent créer des synonymes pour les corriger. Comme il ne semble pas supprimer les index de tracking, Elasticsearch manque de ressources et se bloque.

## Solution

### Mettez à niveau votre version d’ElasticSuite pour pouvoir nettoyer régulièrement les index de tracking.

Une fois que vous avez mis à niveau le plug-in ElasticSuite vers une version supérieure à 2.8.0, vous pouvez configurer un nettoyage périodique des index.

Accédez à **Magasins** > **Configuration** > **Tracking** > **Configuration globale** > **Délai de conservation**

La période de conservation par défaut est de 365 jours. Vous pouvez la réduire à 30 ou 15 jours.

### Mettez à niveau votre version d’ElasticSuite pour utiliser des indices mensuels plutôt que des indices quotidiens

Une fois que vous avez mis à niveau le plug-in ElasticSuite vers la version > 2.9.8 / 2.10.7, les indices de tracking seront basés mensuellement.

Vous pouvez toujours réduire la période de conservation :

Accédez à **Magasins** > **Configuration** > **Tracking** > **Configuration globale** > **Délai de conservation**

La période de rétention par défaut est de 12 mois (générera 12 indices). Vous pouvez le réduire à 3 ou 6 mois.

### Utilisation d’une tâche cron pour nettoyer les données des index de tracking

Créez une tâche cron pour supprimer les index de tracking. Cette commande supprime les index créés au cours du dernier mois :

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Si vous souhaitez supprimer des index à une fréquence définie, créez une tâche cron en vous référant aux articles suivants de notre documentation destinée aux développeurs :

* [Configuration d’une tâche cron personnalisée et d’un groupe cron (tutoriel)](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/crons/custom-cron-tutorial)
* [Configurer les tâches cron](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property)
