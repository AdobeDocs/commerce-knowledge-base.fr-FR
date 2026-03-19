---
title: 'Le cron s’arrête en raison de paramètres incorrectement configurés ou manquants [!DNL OpCache] '
description: Cet article fournit une solution pour les cas où les crons arrêtent de fonctionner en raison de paramètres  [!DNL OpCache]  mal configurés ou manquants.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Cron arrêté en raison de paramètres de [!DNL OpCache] incorrectement configurés ou manquants

Cet article fournit une solution pour le moment où cron cesse de fonctionner en raison de paramètres de [!DNL OpCache] manquants ou mal configurés.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

La couronne a cessé de fonctionner.

## Cause

Le module [!DNL OpCache] a été mis à jour vers une version plus récente qui a introduit un plug-in [!DNL GraphQL] qui réécrit les `env.php` au moment de l’exécution et qui peut remplacer le paramètre cron, ce qui a pu causer le problème. La configuration [!DNL OpCache] doit être mise à jour afin d’éviter tout problème lié au `env.php file`. Ce problème a été résolu dans la [version 2002.1.13](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) du package [!DNL ECE Tools].

## Solution

Option 1 : exécutez la commande suivante dans l’outil de ligne de commande :

```bash
bin/magento cron:run
```

Un message indiquant que le cron est désactivé peut s’afficher.

Option 2 : ouvrez le fichier `app/etc/env.php` - si vous voyez l’élément ci-dessous, alors le cron a été désactivé manuellement, n’a pas été réactivé en raison d’un échec de déploiement ou le problème était lié aux paramètres [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Si le cron est désactivé, exécutez cette commande pour le réactiver : `vendor/bin/ece-tools cron:enable`
1. Assurez-vous d’utiliser la dernière version de [!DNL ECE Tools]. Si ce n’est pas le cas, effectuez une mise à niveau (ou passez à l’élément 3). Pour vérifier votre version existante, exécutez la commande suivante :
   `composer show magento/ece-tools`
1. Si vous utilisez déjà la dernière version de [!DNL ECE Tools], vérifiez la présence du fichier `op-exclude.txt`. Pour ce faire, exécutez la commande suivante :
   `ls op-exclude.txt`.
Si ce fichier n’est pas présent, ajoutez https://github.com/magento/magento-cloud/blob/master/op-exclude.txt à votre référentiel, puis validez la modification et redéployez.
1. Sans avoir à mettre à niveau [!DNL ECE Tools], vous pouvez également simplement ajouter/modifier https://github.com/magento/magento-cloud/blob/master/op-exclude.txt dans votre référentiel, puis valider la modification et redéployer.

## Lecture connexe

* [Problèmes de vérification de l’état de préparation de Cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Propriété Crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [La tâche cron est bloquée au statut « en cours d’exécution »](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
