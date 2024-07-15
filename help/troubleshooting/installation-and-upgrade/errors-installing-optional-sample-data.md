---
title: Erreurs d’installation des exemples de données facultatifs
description: Cette rubrique aborde les solutions aux erreurs que vous pouvez rencontrer lors de l’installation de données d’exemple facultatives.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Erreurs d’installation des exemples de données facultatifs

Cette rubrique aborde les solutions aux erreurs que vous pouvez rencontrer lors de l’installation de données d’exemple facultatives.

## Symptôme (autorisations du système de fichiers)

Erreur dans le journal de la console lors de l’installation des exemples de données à l’aide de l’assistant de configuration :

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Ces exceptions résultent des paramètres des autorisations du système de fichiers.

### Solution

[ Définissez à nouveau la propriété et les autorisations du système de fichiers ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) en tant qu’utilisateur disposant de droits `root`.

## Symptôme (mode de production)

Si vous êtes actuellement défini pour le [mode de production](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html), l’installation des données d’exemple échoue si vous utilisez la commande [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html) :

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Solution

N’installez pas de données d’exemple en mode de production. Passez en mode Développeur, effacez certains répertoires `var` et réessayez.

Saisissez les commandes suivantes dans l’ordre indiqué comme [propriétaire du système de fichiers Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html) :

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Symptôme (sécurité)

Lors de l’installation de données d’exemple facultatives, un message similaire au suivant s’affiche :

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Solution

Lors de l’installation d’exemples de données, désactivez SELinux à l’aide d’une ressource telle que :

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [Documentation CentOS](https://docs.centos.org/en-US/docs/)

## Symptôme (branche de développement)

D’autres erreurs s’affichent, telles que :

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Solution

Il existe des problèmes connus avec l’utilisation de données d’exemple avec la branche de développement Adobe Commerce. Utilisez plutôt la branche principale. Vous pouvez passer à la branche principale comme suit :

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Symptôme (max_execution_time)

L’installation s’arrête avant la fin de l’installation des données d’exemple. Voici un exemple :

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

L’installation des exemples de données ne se termine pas.

Cette erreur se produit lorsque le temps d’exécution maximum configuré de vos scripts PHP est dépassé. Comme le chargement des exemples de données peut prendre un certain temps, vous pouvez augmenter la valeur au cours de l’installation.

### Solution

En tant qu&#39;utilisateur disposant de droits `root`, modifiez `php.ini` pour augmenter la valeur de `max_execution_time` à 600 ou plus. (600 secondes, c’est 10 minutes. Vous pouvez augmenter la valeur à votre convenance.) Une fois l&#39;installation terminée, vous devez restaurer la valeur précédente de `max_execution_time`.

Si vous ne savez pas où se trouve `php.ini`, saisissez la commande suivante :

```php
php --ini
```

La valeur de `Loaded Configuration File` est le `php.ini` que vous devez modifier.

>[!NOTE]
>
>Nous sommes conscients que cet article peut encore contenir des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.
