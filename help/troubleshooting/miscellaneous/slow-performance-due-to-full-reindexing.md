---
title: Lenteur des performances en raison d’une réindexation complète
description: Cet article fournit un correctif pour les mauvaises performances dues à la réindexation complète (où les données des tables de base de données liées à l’indexation sont mises à jour).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Lenteur des performances en raison d’une réindexation complète

Cet article fournit un correctif pour les mauvaises performances dues à la réindexation complète (où les données des tables de base de données liées à l’indexation sont mises à jour).

## Versions et produits concernés

* Adobe Commerce sur l’infrastructure cloud 2.x.x
* Adobe Commerce On-Premise 2.x.x

### Problème

La purge constante et la reconstruction des index sont quelques-unes des raisons de la dégradation des performances. En outre, la réindexation complète continue ajoute des verrous sur les tables, ce qui rend le fonctionnement du site web beaucoup plus lent que prévu.

### Cause

Les actions pouvant générer une réindexation complète ont été effectuées à partir de l’administrateur, notamment :

* Enregistrement de l’attribut de produit
* Enregistrement de la vue de site web/magasin/magasin
* Configuration du magasin

>[!NOTE]
>
>Ces actions doivent être exécutées en dehors des heures de bureau pour s’assurer que ces actions n’affectent pas les performances pendant les heures ouvrables.

[Les extensions tierces](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) peuvent également provoquer une réindexation complète. La réindexation complète peut également être exécutée manuellement à partir de l’interface de ligne de commande. Pour savoir si des index sont réindexés et peuvent entraîner une dégradation des performances :

1. Exécutez cette requête pour rechercher les indexeurs qui ont été entièrement réindexés au cours des 15 dernières minutes :

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Un nom d’indexeur dans la sortie signifie que l’indexeur a été réindexé au moins une fois au cours des 15 dernières minutes.

1. Si vous avez trouvé une réindexation complète fréquente, vérifiez les points suivants :
   * Qui peut effectuer cette opération manuellement à partir de l’interface en ligne de commande
   * Le module tiers effectue la réindexation
   * Ce module tiers marque les indexeurs comme *non valide*

### Solution

Exécutez la réindexation uniquement si nécessaire. Pour connaître les étapes, consultez la section [Configurer les indexeurs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) de la documentation destinée aux développeurs. Une recommandation générale et la bonne pratique consiste à permettre au mécanisme de réindexation partielle de s’occuper de la réindexation des données sans intervention manuelle d’un commerçant. Toutes les réindexation doivent être effectuées à l’aide de la fonctionnalité native d’Adobe Commerce (Mview). Mview effectue une réindexation partielle, qui est la méthode la plus efficace pour réindexer les données. Pour en savoir plus sur Mview, consultez la [présentation de l’indexation : Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) dans notre documentation destinée aux développeurs.

## Lecture connexe

* [Présentation de l’indexation : comment réindexer](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) dans notre documentation destinée aux développeurs.
* [Le cache invalidé entraîne la dégradation du temps de réponse](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md) dans notre base de connaissances de support.
