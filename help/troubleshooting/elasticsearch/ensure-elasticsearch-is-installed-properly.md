---
title: Assurez-vous que l’Elasticsearch est correctement installé
description: Cet article aborde les solutions aux problèmes provoqués par une installation et une configuration d’Elasticsearch incorrectes (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Assurez-vous que l’Elasticsearch est correctement installé

Cet article aborde les solutions aux problèmes provoqués par une installation et une configuration d’Elasticsearch incorrectes (ES).

>[!WARNING]
>
>Sur Adobe Commerce sur l’infrastructure cloud, notez que les mises à niveau de service ne peuvent pas être transférées vers l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production. 48 heures avant que vos modifications ne soient en production, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle vous souhaitez que le processus de mise à niveau démarre.

## Compatibilité des versions Elasticsearch avec Adobe Commerce

* Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud :
   * v2.2.3+ prend en charge ES 5.x
   * Prise en charge de ES 6.x par v2.2.8+ et v2.3.1+
   * ES v2.x et v5.x ne sont pas recommandés en raison de la [fin de vie](https://www.elastic.co/support/eol). Cependant, si vous disposez d’Adobe Commerce v2.3.1 et que vous souhaitez utiliser ES 2.x ou ES 5.x, vous devez [Changer le client php Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).
* Magento Open Source v2.3.0+ prend en charge ES 5.x et 6.x (mais la version 6.x est recommandée).

## Problème

Les symptômes suivants indiquent que l’Elasticsearch n’est pas configuré correctement :

* `Error: No alive nodes in your cluster` - Cette erreur peut apparaître dans les journaux Adobe Commerce :
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * ou dans l’invite (lorsque vous exécutez une réindexation, par exemple)
* Erreurs indiquant que la version de l’Elasticsearch n’est pas compatible avec votre version actuelle d’Adobe Commerce (il s’agit d’une erreur spécifique à l’infrastructure cloud d’Adobe Commerce) :

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Où *version* est le service Elasticsearch s’exécutant dans l’environnement cloud.

## Cause

Elasticsearch n’est pas installé correctement. Cela peut être dû à :

* Une faute de frappe dans le fichier de configuration.
* Version du fichier de configuration qui ne correspond à aucune version de l’Elasticsearch installé pour l’environnement.
* Une version correctement installée dans l’environnement, correctement configurée dans le fichier de configuration, mais qui n’est pas une version prise en charge pour la version actuellement installée d’Adobe Commerce.

## Solution

Pour configurer correctement l’Elasticsearch :

* Les commerçants sur Adobe Commerce sur l’infrastructure cloud peuvent suivre les étapes de notre documentation destinée aux développeurs : [Configuration du service Elasticsearch](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-elastic.html).
* Les commerçants sur Adobe Commerce sur site et Magento Open Source peuvent suivre les étapes de notre documentation destinée aux développeurs : [Installation et configuration de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Après avoir configuré l’Elasticsearch, vérifiez qu’il est correctement configuré :

1. Connectez-vous à votre serveur .
1. Vérifiez le numéro de version de Elasticsearch (2.x, 5.x ou 6.x) dans la sortie de l&#39;exécution de la commande : `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Par exemple, dans Adobe Commerce sur l&#39;infrastructure cloud : `curl -XGET localhost:9200`
1. Vérifiez ce qui est configuré dans Adobe Commerce sur la configuration de l’infrastructure cloud en exécutant la commande : `php bin/magento config:show catalog/search`
1. Vérifiez `catalog/search/engine` et qu&#39;il correspond au numéro de version de l&#39;Elasticsearch. Par exemple, dans Adobe Commerce sur l’infrastructure cloud :
   * Elasticsearch 5.X - élasticsearch5
   * Elasticsearch 6.X - élasticsearch6
   * Elasticsearch 2.X - élasticsearch
1. Vérifiez `index_prefix`. Si vous avez plusieurs environnements, assurez-vous d’avoir des valeurs `index_prefix` différentes pour eux.
