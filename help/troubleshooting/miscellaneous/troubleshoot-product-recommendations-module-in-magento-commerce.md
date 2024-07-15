---
title: Dépannage du module Recommendations de produit dans Adobe Commerce
description: Cet article présente les suggestions de dépannage pour la
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Dépannage du module Recommendations de produit dans Adobe Commerce

Cet article présente les suggestions de dépannage pour la

```php
magento/product-recommendations
```

module et sa dépendance

```php
saas-export
```

, car vous avez besoin que les deux modules fonctionnent afin d’utiliser l’outil Recommendations du produit dans Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce 2.4.4 - 2.4.7

## Dépannage du module de recommandations de produits

Si vous avez configuré la variable

```php
magento/product-recommendations
```

module correctement (consultez [Recommendations du produit - Installation et configuration de Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) dans notre documentation destinée aux développeurs.), mais vous ne voyez aucune recommandation, essayez ce qui suit :

* Il est possible que le module n’ait pas eu assez de temps pour collecter des données comportementales. Permet au système de fonctionner pendant 24 heures afin de pouvoir commencer à collecter des données. Envisagez de déployer un type de recommandation qui ne nécessite aucune donnée comportementale, telle que &quot;Plus comme ceci&quot;.

* Si vous ne voyez pas les recommandations que vous avez configurées, il est possible qu’il n’y ait pas encore suffisamment de données pour créer des recommandations pour l’utilisateur.

* Assurez-vous que l’espace de données SaaS ou la clé API sont valides. Si vous obtenez une erreur après avoir spécifié votre espace de données SaaS ou votre clé API lors de l’initialisation des recommandations de produits, vérifiez que vous avez correctement saisi l’[espace de données SaaS et la clé API](https://docs.magento.com/user-guide/configuration/services/saas.html) (dans notre guide d’utilisation). Pour garantir que MageID et la clé API sont liés, l’utilisateur propriétaire de MageID, généralement l’utilisateur propriétaire de la licence Adobe Commerce, doit être le même utilisateur qui génère la clé API. Si vous devez modifier le MageID utilisé, [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Si le [mode de restriction des cookies](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) (dans notre guide de l’utilisateur) est activé, Adobe Commerce ne collecte les données comportementales qu’avec le consentement de l’acheteur. Si le mode Restriction des cookies est désactivé, Adobe Commerce collecte les données comportementales par défaut.

## Module d’exportation SaaS du catalogue

Pour les problèmes liés à l’exportation SaaS du catalogue (

```php
saas-export
```

) :

1. Vérifiez que les tâches [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (dans notre documentation destinée aux développeurs) sont en cours d’exécution.
1. Vérifiez que les [indexers](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (dans notre documentation destinée aux développeurs) sont en cours d’exécution et que la variable    ```php    Product Feed    ```    l’indexeur est défini sur    ```php    Update by Schedule    ```    .
1. Vérifiez que les modules sont activés. La variable    ```php    saas-export    ```    metapackage installe les modules suivants, qui doivent tous être activés :    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Consultez les [logs](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (dans notre documentation destinée aux développeurs). Assurez-vous qu’aucune erreur n’est associée aux modules ci-dessus.
1. Actualisez le cache de configuration. Accédez à **Système** > **Outils** > **Gestion du cache** , puis effacez le cache de configuration.
1. Vérifiez qu’il existe des données dans la variable    ```php    catalog_data_exporter_products    ```    table de base de données.

## Événements

[Événements de recommandation](https://devdocs.magento.com/recommendations/verify.html), dans notre documentation destinée aux développeurs, décrit les événements comportementaux envoyés à Adobe Commerce.

## Lecture connexe

* [Recommendations du produit - Aperçu](https://devdocs.magento.com/recommendations/product-recs.html) dans notre documentation destinée aux développeurs
* [Recommendations du produit - Installation et configuration de Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) dans notre documentation destinée aux développeurs
* [Marketing - Recommendations produit](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) dans notre guide d’utilisation
* [Créer un produit Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) dans notre guide d’utilisation
