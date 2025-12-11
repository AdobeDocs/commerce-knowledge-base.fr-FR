---
title: Performances lentes en raison d’une réindexation complète
description: Cet article fournit un correctif pour les mauvaises performances dues à une réindexation complète (où les données des tables de base de données liées à l’indexation sont mises à jour).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 0786763a1db386fbea7f809eba9bc7f202cdd27a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Performances lentes en raison d’une réindexation complète

Cet article fournit un correctif pour les mauvaises performances dues à une réindexation complète (où les données des tables de base de données liées à l’indexation sont mises à jour).

## Versions et produits concernés

* Adobe Commerce sur l’infrastructure cloud 2.x.x
* Adobe Commerce on-premise 2.x.x

### Problème

Le vidage constant et la reconstruction de l’index sont quelques-unes des raisons de la dégradation des performances. En outre, la réindexation complète constante ajoute des verrous sur les tableaux, ce qui ralentit considérablement le fonctionnement du site web.

### Cause

Les actions qui peuvent produire une réindexation complète ont été effectuées par l’administrateur, notamment :

* Enregistrement de l’attribut de produit
* Enregistrement de la vue du site web/magasin/magasin
* Configuration de la boutique

>[!NOTE]
>
>Ces actions doivent être exécutées en dehors des heures de bureau afin de vous assurer qu’elles n’affectent pas les performances pendant ces heures.

[Les extensions tierces](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) peuvent également entraîner une réindexation complète. La réindexation complète peut également être exécutée manuellement à partir de l’interface de ligne de commande. Pour déterminer si des index sont réindexés et peuvent entraîner une dégradation des performances :

1. Exécutez cette requête pour rechercher les indexeurs qui ont été entièrement réindexés au cours des 15 dernières minutes :

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Un nom d’indexeur dans la sortie signifie que l’indexeur a été réindexé au moins une fois au cours des 15 dernières minutes.

1. Si vous constatez des réindexations complètes fréquentes, vérifiez les points suivants :
   * Qui peut effectuer cette opération manuellement à partir de l’interface en ligne de commande ?
   * Quel module tiers effectue la réindexation ?
   * Quel module tiers marque les indexeurs comme *non valides*

### Solution

Exécutez la réindexation uniquement lorsque cela est nécessaire. Pour connaître les étapes, consultez [Configuration des indexeurs](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) dans notre documentation destinée aux développeurs. Une recommandation générale et une bonne pratique consiste à permettre au mécanisme de réindexation partielle de prendre en charge la réindexation des données sans aucune action manuelle requise de la part d&#39;un commerçant. Toute réindexation doit être effectuée à l’aide de la fonctionnalité Adobe Commerce native (Mview). Mview effectue une réindexation partielle, qui est le moyen le plus efficace de réindexer les données. Pour en savoir plus sur Mview, consultez la section [Présentation de l’indexation : Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) dans notre documentation destinée aux développeurs et développeuses.

## Lectures connexes

* [Aperçu de l’indexation : comment effectuer une réindexation &#x200B;](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) dans notre documentation destinée aux développeurs.


