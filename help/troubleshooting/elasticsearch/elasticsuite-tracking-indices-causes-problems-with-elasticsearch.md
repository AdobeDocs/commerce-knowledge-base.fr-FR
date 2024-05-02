---
title: Les index de suivi ElasticSuite entraînent des problèmes avec Elasticsearch
description: Cet article traite des problèmes de mémoire Elasticsearch causés par les indices de suivi produits par le module externe ElasticSuite.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Les index de suivi ElasticSuite entraînent des problèmes avec Elasticsearch

>[!NOTE]
>
>ElasticSuite et ses applications affiliées sont des outils tiers non actuellement pris en charge par Adobe. Ce contenu est présenté à titre d’information uniquement et non comme une indication de ce qui est activé pour la couverture d’assistance.

Cet article traite des problèmes de mémoire Elasticsearch causés par les indices de suivi produits par le module externe ElasticSuite.

## Produits et versions concernés

Les versions d’ElasticSuite antérieures à la version 2.8.0 ne peuvent pas nettoyer régulièrement les index de suivi.

Les versions d’ElasticSuite antérieures à la version 2.9.8 / 2.10.7 stockent les index de suivi dans des index quotidiens, ce qui entraîne une augmentation du nombre d’index ouverts.

## Problème

Si le module externe tiers d’ElasticSuite est installé, vous pouvez rencontrer des problèmes de mémoire Elasticsearch et le service Elasticsearch peut se bloquer suite aux index de suivi d’ElasticSuite. Les symptômes incluent :

* Elasticsearch se bloque sans erreur de mémoire.
* Lors de l’exécution d’une commande d’intégrité `curl -m1 localhost:9200/_cluster/health?pretty` ou `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (pour les comptes de démarrage) il y a des centaines ou des milliers `unassigned_shards`
* Les performances des Elasticsearch ou des sites sont fortement dégradées.
* *&quot;Aucun noeud vivant trouvé dans votre grappe&quot;* dans déploiement Elasticsearch ou erreurs de journal.
* *&quot;Rejet de la mise à jour du mapping vers [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* dans les erreurs de déploiement ou de journal.

## Cause

ElasticSuite dispose d’une nouvelle fonctionnalité qui crée des index de suivi. Ces indices de suivi enregistrent les termes de recherche les plus utilisés, les termes qui génèrent le plus de chiffre d’affaires et les termes qui mènent à une page de résultats nulle, de sorte que les marchands puissent créer des synonymes pour les corriger. Il ne semble pas supprimer les index de suivi, de sorte que les Elasticsearch manquent de ressources et se bloquent.

## Solution

### Mettez à niveau votre version d’ElasticSuite pour pouvoir nettoyer régulièrement les index de suivi.

Une fois que vous avez mis à niveau le module externe ElasticSuite vers une version supérieure à 2.8.0, vous pouvez configurer un nettoyage périodique des index.

Accédez à **Magasins** > **Configuration** > **Tracking** > **Configuration globale** > **Retard de rétention**

La période de conservation par défaut est de 365 jours. Vous pouvez la réduire à 30 ou 15 jours.

### Mettez à niveau votre version d’ElasticSuite pour utiliser des index mensuels plutôt que des index quotidiens.

Une fois que vous avez mis à niveau le module externe ElasticSuite vers la version > 2.9.8 / 2.10.7, les index de suivi seront basés sur un mois.

Vous pouvez tout de même réduire la période de rétention :

Accédez à **Magasins** > **Configuration** > **Tracking** > **Configuration globale** > **Retard de rétention**

La période de conservation par défaut est de 12 mois (12 indices seront générés). Vous pouvez le réduire à 3 ou 6 mois.

### Utiliser une tâche cronjob pour nettoyer les données des index de suivi

Créez une tâche cron pour supprimer les index de suivi. Cette commande supprime les index créés au cours du dernier mois :

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Si vous souhaitez supprimer des index à une fréquence définie, créez une tâche cron en vous reportant aux articles suivants de notre documentation destinée aux développeurs :

* [Configuration d’une tâche cron personnalisée et d’un groupe cron (tutoriel)](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [Configuration de tâches cron](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
