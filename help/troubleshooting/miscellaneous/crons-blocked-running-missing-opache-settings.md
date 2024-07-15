---
title: Cron s’arrête en raison de paramètres mal configurés ou manquants. [!DNL OpCache]
description: Cet article fournit une solution lorsque les crons cessent de fonctionner en raison de paramètres mal configurés ou manquants. [!DNL OpCache]
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron arrêté en raison de paramètres incorrects ou manquants de [!DNL OpCache]

Cet article fournit une solution pour le cas où cron cesse de fonctionner en raison de paramètres [!DNL OpCache] manquants ou mal configurés.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

Le cron a cessé de fonctionner.

## Cause

Le module [!DNL OpCache] a été mis à jour vers une version plus récente qui a introduit un module externe [!DNL GraphQL] qui réécrit l’élément `env.php` lors de l’exécution et peut remplacer le paramètre cron, ce qui a pu entraîner le problème. La configuration [!DNL OpCache] doit être mise à jour pour éviter tout problème avec `env.php file`, et cela a été résolu dans [version 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) du package [!DNL ECE Tools].

## Solution

Option 1 : exécutez ce qui suit dans l’outil de ligne de commande :

```bash
bin/magento cron:run
```

Un message peut s’afficher indiquant que le cron est désactivé.

Option 2 : ouvrez le fichier `app/etc/env.php` : si vous voyez ci-dessous, le cron a été désactivé manuellement, n’a pas été réactivé en raison d’un déploiement en échec ou le problème était lié aux paramètres [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Si le cron est désactivé, exécutez cette commande pour réactiver le cron : `vendor/bin/ece-tools cron:enable`
1. Assurez-vous que vous utilisez la dernière version de [!DNL ECE Tools]. Si ce n’est pas le cas, effectuez une mise à niveau (ou passez à l’élément 3). Pour vérifier votre version existante, exécutez la commande suivante :
   `composer show magento/ece-tools`
1. Si vous utilisez déjà la dernière version de [!DNL ECE Tools], vérifiez la présence du fichier `op-exclude.txt`. Pour cela, exécutez la commande suivante :
   `ls op-exclude.txt`.
Si ce fichier n’est pas présent, ajoutez https://github.com/magento/magento-cloud/blob/master/op-exclude.txt à votre référentiel, puis validez la modification et redéployez.
1. Sans avoir à effectuer la mise à niveau [!DNL ECE Tools], vous pouvez également ajouter/modifier https://github.com/magento/magento-cloud/blob/master/op-exclude.txt dans votre référentiel, puis valider la modification et redéployer.

## Lecture connexe

* [Problèmes de vérification de l’état de préparation Cron](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Propriété Cron](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [La tâche Cron est bloquée dans l’état &quot;en cours d’exécution&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
