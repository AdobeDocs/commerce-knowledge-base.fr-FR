---
title: Le déploiement échoue en raison de l’incompatibilité du module Fastly avec la version Adobe Commerce
description: 'MISE À JOUR : 29 février 2019'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%
---
# Le déploiement échoue en raison de l’incompatibilité du module Fastly avec la version Adobe Commerce

MISE À JOUR : 29 février 2019

Cet article fournit un correctif pour le cas où le déploiement échoue, car le module Fastly est incompatible avec votre version actuelle d’Adobe Commerce.

**Problème :** le déploiement échoue après une nouvelle validation et une nouvelle notification push, avec un message d’erreur similaire à ce qui suit :

>\[Exception\] Avertissement : argument 3 manquant pour Fastly\\Cdn\\Plugin\\..., appelé dans /app/vendor/magento/framework/Interception/Interceptor.php ... et défini dans /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Cause :** modifications rétrocompatibles dans le module Fastly version 1.2.79.

**Solution (temporaire) :** mettez à niveau le module Fastly vers la version 1.2.82 ou une version ultérieure et chargez un nouveau VCL dans Commerce Admin. Ensuite, validez et transmettez vos modifications pour déclencher un déploiement réussi.

## Versions affectées

* Adobe Commerce On-premise 2.1.X
* Adobe Commerce sur l’infrastructure cloud 2.1.X
* Module Fastly 1.2.79

## Problème

Lorsque vous validez et envoyez vos modifications à l’environnement d’intégration, de production ou d’évaluation, l’étape suivante consiste généralement à déclencher le processus de déploiement. Cette opération est effectuée automatiquement dans l’édition de l’infrastructure cloud d’Adobe Commerce et manuellement dans Adobe Commerce On-Premise.

Le déploiement peut échouer avec les messages d’erreur suivants :

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Si vous utilisez la solution Adobe Commerce sur l’infrastructure cloud, ce message d’erreur s’affiche dans le [journal de déploiement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/test/log-locations). Pour Adobe Commerce On-Premise, l’erreur s’affiche dans la ligne de commande.

## Cause

Le problème est dû aux modifications rétrocompatibles dans le module Fastly v1.2.79.

## Solution

Mettez à niveau le module Fastly vers la version 1.2.82 ou une version ultérieure.

Pour ce faire, procédez comme suit :

1. Exécutez l’une des commandes suivantes :
   * si le module Fastly est inclus dans le métapaquet magento-cloud :    <pre>mise à jour du compositeur magento/magento-cloud-metapackage</pre>
   * si le module Fastly a été installé séparément (par exemple, si vous utilisez Adobe Commerce on-premise, et non l’édition cloud) <pre>mise à jour rapide du compositeur/magento2</pre>
1. Validez et envoyez les modifications, et déclenchez le processus de déploiement s’il n’est pas effectué automatiquement.
1. Dans l’administrateur, [chargez le nouveau VCL sur Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
