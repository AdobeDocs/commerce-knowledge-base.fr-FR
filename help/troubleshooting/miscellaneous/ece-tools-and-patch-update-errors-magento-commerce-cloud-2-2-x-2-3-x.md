---
title: ETC-Outils et erreurs de mise à jour de correctif infrastructure cloud Adobe Commerce 2.2.x, 2.3.x
description: Cet article fournit une solution au problème où des messages d’erreur s’affichent, y compris "*failed to open stream:*" ou "*No such file or directory*" lors de la tentative de déploiement de mises à jour dans les outils ECE, les correctifs ou d’autres modifications.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ETC-Outils et erreurs de mise à jour de correctif infrastructure cloud Adobe Commerce 2.2.x, 2.3.x

Cet article fournit une solution au problème où vous voyez des messages d’erreur comprenant &quot;*échec de l’ouverture du flux :*&quot; ou &quot;*Aucun fichier ou répertoire de ce type*&quot; lorsque vous essayez de déployer des mises à jour sur les outils de la CEE, les correctifs ou d&#39;autres modifications.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

Erreurs lors du déploiement de mises à jour dans les outils ECE, correctifs ou autres modifications : erreurs PHP dans la console cloud et dans la `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Erreurs du journal des exceptions :

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Cause

Mauvaise configuration de votre `composer.json` fichier .

## Solution

Si un paramètre est manquant dans votre `composer.json` , certains répertoires ne seront pas copiés à partir de la base de code Adobe Commerce. Le package et la mise à jour/le correctif ne peuvent pas s’appliquer, car les fichiers sont introuvables.

Veuillez modifier votre section supplémentaire pour qu’elle corresponde à celle fournie ci-dessous et relancer le déploiement.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Lecture connexe

* [Mises à niveau et correctifs](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade-parent.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=update%20ece%20tools) dans notre documentation destinée aux développeurs.
