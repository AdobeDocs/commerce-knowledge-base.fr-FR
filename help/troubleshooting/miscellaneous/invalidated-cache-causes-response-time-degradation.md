---
title: Le cache invalidé entraîne une dégradation du temps de réponse.
description: Cet article fournit une solution pour éviter l’invalidation du cache, qui peut entraîner la lenteur des performances d’un magasin Adobe Commerce.
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Le cache invalidé entraîne une dégradation du temps de réponse.

Cet article fournit une solution pour éviter l’invalidation du cache, qui peut entraîner la lenteur des performances d’un magasin Adobe Commerce.

PRODUITS ET VERSIONS AFFECTÉS :

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

Réponse lente du site.

## Cause

Un temps de réponse long peut être dû à l’invalidation du cache (purgé).

Le cache est utilisé pour générer des réponses rapides aux demandes des visiteurs du site. Si aucune donnée de cache appropriée n’est disponible, l’application Adobe Commerce récupère les données de la base de données, calcule et agrège les données, puis les stocke dans le cache de stockage. Le processus de génération du cache nécessite des ressources système supplémentaires, ce qui entraîne une dégradation totale du temps de réponse.

Il existe deux types de cache dans Adobe Commerce :

1. Interne :
   * stocke les données sur le serveur ;
   * stocke des données spécifiques (configuration, détails du produit, détails de la catégorie, etc.)
1. Externe :
   * CDN ou vernis (dans le cas d’Adobe Commerce sur l’infrastructure cloud - CDN Fastly)
   * stocke des pages complètes déjà générées. Par exemple, les pages catalogue/catégorie, catalogue/produit, etc.

### Vérifier si le cache est invalidé

Vous trouverez des informations concernant les types de cache invalidés dans la section `<install_directory>/var/log/debug.log` fichier .

Pour ce faire :

1. Ouvrir `<install_directory>/var/log/debug.log`
1. Recherchez &quot; *cache\_invalidate* &quot;.
1. Vérifiez ensuite la balise spécifiée. Il indique le cache qui a été vidé. Vous pouvez rencontrer des problèmes en raison du cache invalidé si vous voyez une balise sans identifiant d’entité spécifique spécifié, par exemple :
   * `cat_p` : signifie cache de produit de catalogue.
   * `cat_c` - cache de catégorie de catalogue.
   * `FPC` : cache de la page entière.
   * `CONFIG` - cache de configuration.

   Le fait que l&#39;un d&#39;entre eux ait été vidé ralentirait la réaction du site. Si la balise contient un identifiant d’entité, par exemple : `category_product_1258`, cela indique le cache d’un produit ou d’une catégorie spécifique, etc. Le vidage du cache d’un produit ou d’une catégorie spécifique n’entraînait pas une diminution significative du temps de réponse.

Voici un exemple d’un `debug.log` contenant des enregistrements sur la variable `cat_p` et `category_product_15044` mémoire cache ayant été vidée :

![exemple de contenu debug.log](assets/debug_log_sample.png)

En règle générale, le cache est invalidé en raison des éléments suivants :

* Réindexation complète.
* Videz le cache à partir de l’interface de ligne de commande, manuellement ou à l’aide de cron.

## Recommandation

1. Évitez de vider le cache de l’interface de ligne de commande de Commerce.
1. Configuration des indexeurs sur **Mise à jour par planification** au lieu de **Mise à jour en mode d’enregistrement** car ce dernier déclenche une réindexation complète. À titre de référence, voir [Gestion des indexeurs > Configuration des indexeurs](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers) dans notre documentation destinée aux développeurs.
