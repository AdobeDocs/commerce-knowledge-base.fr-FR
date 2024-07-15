---
title: Réinitialiser le thème par défaut
description: Selon les problèmes que vous pouvez rencontrer lors de la personnalisation de vos thèmes et du développement de votre boutique, vous n’avez peut-être pas accès via l’administrateur Commerce. Vous pouvez effacer et réinitialiser la valeur par défaut de votre thème sans accéder à l’administrateur. Une fois que vous avez effacé le thème, le thème Luma par défaut est appliqué.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Réinitialiser le thème par défaut

Selon les problèmes que vous pouvez rencontrer lors de la personnalisation de vos thèmes et du développement de votre boutique, vous n’avez peut-être pas accès via l’administrateur Commerce. Vous pouvez effacer et réinitialiser la valeur par défaut de votre thème sans accéder à l’administrateur. Une fois que vous avez effacé le thème, le thème Luma par défaut est appliqué.

Pendant que vous développez Adobe Commerce (tous les déploiements) et les composants de Magento Open Source (modules, thèmes et modules de langue), votre environnement en rapide évolution nécessite que vous effaciez régulièrement certains répertoires et caches. Sinon, votre code s’exécute avec des exceptions et ne fonctionnera pas correctement. Pour plus d’informations, voir [Effacer les répertoires pendant le développement](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html) dans notre documentation destinée aux développeurs.

## Environnement et technologies

* Adobe Commerce sur site
* Adobe Commerce sur l’infrastructure cloud
* Magento Open Source

## Conditions préalables

* Outils de base de données

## Étapes

Si vous devez réinitialiser le thème de magasin, mais ne pouvez pas accéder au panneau d’administration, vous pouvez le réinitialiser dans la base de données en procédant comme suit :

1. Utilisez un outil de base de données tel que [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) ou accédez manuellement à la base de données à partir de la ligne de commande pour exécuter la requête SQL suivante : `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Effacez les répertoires suivants :
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Ainsi, aucun thème n’est défini au niveau de la vue du magasin. Lorsque vous rechargez les pages d’accueil du magasin, le thème Luma par défaut est appliqué.

## Informations supplémentaires

* [Effacer les répertoires pendant le développement](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html) dans notre documentation destinée aux développeurs
