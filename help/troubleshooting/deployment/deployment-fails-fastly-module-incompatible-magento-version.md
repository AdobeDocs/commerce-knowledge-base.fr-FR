---
title: Échec du déploiement Version Adobe Commerce incompatible avec le module Fasting
description: "MISE À JOUR : 29 février 2019"
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Échec du déploiement Version Adobe Commerce incompatible avec le module Fasting

MISE À JOUR : 29 février 2019

Cet article fournit un correctif pour en cas d’échec du déploiement, car le module Fastly est incompatible avec votre version actuelle d’Adobe Commerce.

**Problème :** Le déploiement échoue après une nouvelle validation et transmission push, avec un message d’erreur similaire à ce qui suit :

>\[Exception\] Avertissement : argument 3 manquant pour Fastly\\Cdn\\Plugin\\..., appelé dans /app/vendor/magento/framework/Interception/Interceptor.php ... et défini dans /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Cause :** modifications incompatibles en amont dans le module Fastly v1.2.79.

**Solution (temporaire) :** mettez à niveau le module Fastly vers la version 1.2.82 ou ultérieure et chargez un nouveau VCL dans l’administrateur Commerce. Ensuite, validez et poussez vos modifications pour déclencher un déploiement réussi.

## Versions affectées

* Adobe Commerce On-Premise 2.1.X
* Adobe Commerce sur l’infrastructure cloud 2.1.X
* Module Fastly 1.2.79

## Problème

Lorsque vous validez et poussez vos modifications dans l’environnement d’intégration, de production ou d’évaluation, en règle générale, l’étape suivante déclenche le processus de déploiement. Cette opération est effectuée automatiquement dans Adobe Commerce sur l’édition de l’infrastructure cloud et manuellement dans Adobe Commerce sur site.

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

Si vous utilisez Adobe Commerce sur la solution d’infrastructure cloud, ce message d’erreur s’affiche dans le [log de déploiement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/test/log-locations). Pour Adobe Commerce On-Premise, l’erreur s’affiche dans la ligne de commande.

## Cause

Le problème est dû aux modifications incompatibles en amont dans le module Fastly v1.2.79.

## Solution

Mettez à niveau le module Fastly vers la version 1.2.82 ou ultérieure.

Pour ce faire, procédez comme suit :

1. Exécutez l’une des commandes suivantes :
   * si le module Fastly est inclus dans le package magento-cloud-metapackage :    <pre>mise à jour du compositeur magento/magento-cloud-metapackage</pre>
   * si le module Fastly a été installé séparément (par exemple, si vous utilisez Adobe Commerce sur site, et non l’édition cloud) ; <pre>mise à jour rapide/magento2 du compositeur</pre>
1. Validez et envoyez les modifications, puis déclenchez le processus de déploiement si ce n’est pas fait automatiquement.
1. Dans l’Admin, [chargez le nouveau VCL sur Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
