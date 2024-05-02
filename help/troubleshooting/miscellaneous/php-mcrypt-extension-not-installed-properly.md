---
title: L’extension de chiffrement PHP n’est pas installée correctement
description: L’extension de chiffrement PHP n’est pas installée correctement
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# L’extension de chiffrement PHP n’est pas installée correctement

>[!WARNING]
>
>REMARQUE : la fonction de chiffrement de la bibliothèque était [obsolète de PHP 7.1 et a été supprimé de PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Détail

Les erreurs peuvent être les suivantes :

```php
exception 'Exception' with message 'PHP Warning: [PHP](https://glossary.magento.com/php) Startup: Unable to load dynamic [library](https://glossary.magento.com/library) '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] [exception](https://glossary.magento.com/exception) 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://glossary.magento.com/extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Description

En particulier sur les systèmes de développement qui incluent une &quot;pile&quot; Linux/Apache/MySQL/PHP (LAMP) distincte du système d’exploitation, il est possible que mcrypt ne soit pas du tout installé ou qu’il soit installé dans le chemin d’accès de la pile LAMP, mais pas dans celui du système d’exploitation.

Par conséquent, le programme d’installation d’Adobe Commerce ne peut pas localiser l’extension et l’installation échoue.

## Suggestion

Déterminez si l’extension mcrypt est chargée de l’une des manières suivantes :

* Configurez une [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) dans le répertoire racine du serveur web et examinez la sortie dans un navigateur web.
* Exécutez la commande suivante :    `$ php -r "phpinfo();" | grep mcrypt`

Si mcrypt est *not* installés, des messages similaires à l’affichage suivant :

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

Dans certains cas, vous devrez peut-être installer le logiciel Adobe Commerce à partir du [ligne de commande](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html) et indiquez le chemin d’accès complet à la pile LAMP installée.
