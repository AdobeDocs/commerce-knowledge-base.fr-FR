---
title: L’extension de chiffrement PHP n’est pas installée correctement
description: L’extension de chiffrement PHP n’est pas installée correctement
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# L’extension de chiffrement PHP n’est pas installée correctement

>[!WARNING]
>
>REMARQUE : La fonctionnalité de bibliothèque de chiffrement a été [ obsolète de PHP 7.1 et a été supprimée de PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Détail

Les erreurs peuvent être les suivantes :

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/fr/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
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

* Configurez un fichier [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) dans le répertoire racine du serveur web et examinez la sortie dans un navigateur web.
* Exécutez la commande suivante :    `$ php -r "phpinfo();" | grep mcrypt`

Si mcrypt n’est *pas* installé, des messages similaires à l’affichage suivant :

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

Dans certains cas, vous devrez peut-être installer le logiciel Adobe Commerce à partir de la [ligne de commande](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/advanced) et spécifier le chemin d’accès complet à la pile LAMP installée.
