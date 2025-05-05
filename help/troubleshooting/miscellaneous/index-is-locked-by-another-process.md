---
title: L’index est verrouillé par un autre processus.
description: Cet article traite d’un problème d’indexation courant dans Adobe Commerce, où l’index est verrouillé par un autre processus et ignoré.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# L’index est verrouillé par un autre processus.

Cet article traite d’un problème d’indexation courant dans Adobe Commerce, où l’index est verrouillé par un autre processus et ignoré.

## Produits et versions concernés

* Adobe Commerce 2.X

## Problème

Lors d&#39;une réindexation complète dans votre interface de ligne de commande, Adobe Commerce vous envoie le message d&#39;erreur : *&#39;Index est verrouillé par un autre processus de réindexation. Sauter.&#39;* En d’autres termes, lorsque le processus ou le type d’index est verrouillé, vous ne pouvez pas réindexer ce type d’index verrouillé particulier. La réindexation ignore toujours ce type d’index.

## Cause

Cette erreur peut se produire si l’index précédent n’a pas été terminé avec succès. Voici quelques raisons possibles :

* Le processus a été interrompu par un autre processus ou un autre utilisateur.
* Limite de mémoire.
* Erreur MySQL, comme un délai d’expiration.
* Erreur PHP fatale lors de la réindexation.

## Étapes à reproduire

1. Par exemple, indiquez que la variable    ```bash    cataloginventory_stock ```    le type d’index est verrouillé.
1. Lorsque vous essayez de réindexer toutes les données en exécutant la commande d’interface de ligne de commande    ```bash    php bin/magento indexer:reindex    ```, vous obtiendrez le résultat de sortie suivant :    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Comme vous pouvez le voir ci-dessus, la variable    ```bash    cataloginventory_stock```    Le processus d’index a été ignoré.


## Solution

Vous devez réinitialiser l’état de l’index, puis essayer d’exécuter le nouveau processus de réindexation. Pour réinitialiser l’état de l’index, vous devez exécuter la commande :

```bash
bin/magento indexer:reset <index identifier>
```

Si vous ne savez pas quels sont les identifiants d’index (code), vous pouvez les lister à l’aide de la commande :

```bash
bin/magento indexer:info
```

Pour des raisons d’exhaustivité, voici toutes les combinaisons possibles pour les index natifs :

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Lecture connexe

Dans notre base de connaissances de soutien :

* [Les tâches Cron verrouillent les tâches d’autres groupes (Adobe Commerce sur l’infrastructure cloud).](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

Dans notre guide d’utilisation :

* [Gestion des index](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

Dans notre documentation destinée aux développeurs :

* [Présentation de l’indexation](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Meilleures pratiques des indexeurs](https://experienceleague.adobe.com/fr/docs/commerce-operations/performance-best-practices/configuration)
* [Configurer Et Exécuter Cron](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [Gérer Les Indexateurs](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [Indexer Optimization](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
