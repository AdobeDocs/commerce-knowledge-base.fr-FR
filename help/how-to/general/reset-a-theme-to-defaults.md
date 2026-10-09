---
title: Réinitialiser un thème aux valeurs par défaut
description: Selon les problèmes que vous pouvez rencontrer lors de la personnalisation de vos thèmes et du développement de votre boutique, vous ne disposez peut-être pas d’un accès via l’administrateur Commerce. Vous pouvez effacer et réinitialiser votre thème par défaut sans accéder à l’administrateur. Une fois le thème effacé, le thème Luma par défaut est appliqué.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%
---
# Réinitialiser un thème aux valeurs par défaut

Selon les problèmes que vous pouvez rencontrer lors de la personnalisation de vos thèmes et du développement de votre boutique, vous ne disposez peut-être pas d’un accès via l’administrateur Commerce. Vous pouvez effacer et réinitialiser votre thème par défaut sans accéder à l’administrateur. Une fois le thème effacé, le thème Luma par défaut est appliqué.

Pendant que vous développez des composants Adobe Commerce (tous les déploiements) et Magento Open Source (modules, thèmes et packages de langue), votre environnement en rapide évolution nécessite que vous effaciez périodiquement certains répertoires et caches. Dans le cas contraire, votre code s’exécute avec des exceptions et ne fonctionnera pas correctement. Pour plus d’informations, consultez [Effacer les répertoires pendant le développement](https://developer.adobe.com/commerce/php/development/components/clear-directories/) dans notre documentation destinée aux développeurs.

## Environnement et technologies

* Adobe Commerce On-Premise
* Adobe Commerce sur les infrastructures cloud
* Magento Open Source

## Conditions préalables

* Outils de base de données

## Étapes

Si vous devez réinitialiser le thème du magasin, mais que vous ne pouvez pas accéder au panneau d’administration, vous pouvez le réinitialiser dans la base de données en procédant comme suit :

1. Utilisez un outil de base de données tel que [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou accédez à la base de données manuellement à partir de la ligne de commande pour exécuter la requête SQL suivante : `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Effacez les répertoires suivants :
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Ainsi, aucun thème ne sera défini au niveau de l’affichage du magasin et, lorsque vous rechargez les pages de garde du magasin, le thème Luma par défaut sera appliqué.

## Informations Supplémentaires

* [Effacer les répertoires pendant le développement](https://developer.adobe.com/commerce/php/development/components/clear-directories/) dans notre documentation destinée aux développeurs
