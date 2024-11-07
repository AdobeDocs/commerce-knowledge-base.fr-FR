---
title: Lors de l’installation, exception SessionHandler::read()
description: "Cet article fournit un correctif pour une erreur **SessionHandler::read()** d’exception lors de l’installation d’Adobe Commerce."
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Lors de l’installation, exception SessionHandler::read()

Cet article fournit un correctif pour une erreur **SessionHandler::read()** d’exception lors de l’installation d’Adobe Commerce.

## Problème

Lors de la dernière étape d’installation d’Adobe Commerce, l’exception suivante s’affiche :

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Cette erreur survient uniquement dans les versions de code antérieures au 28 septembre 2015. Si vous installez le code du 29 septembre ou une date ultérieure, cette erreur ne doit pas se produire. Pour plus d’informations sur les options de configuration pour Redis, voir [Configuration de Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) dans notre documentation destinée aux développeurs. Pour plus d’informations sur la spécification de Redis à l’aide du programme d’installation de ligne de commande, consultez la [rubrique d’installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) ou la [ rubrique de configuration de déploiement](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment) dans notre documentation destinée aux développeurs.

## Cause

Cela se produit lorsque votre paramètre `session.save_handler` PHP est défini sur un autre stockage de session que `files` (par exemple, `redis`, `memcached`, etc.). C&#39;est un problème connu que nous travaillons à résoudre.

## Solutions :

* Mettez à niveau votre code Adobe Commerce. Reportez-vous au [Guide d&#39;installation > Mise à jour du logiciel Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall) dans notre documentation destinée aux développeurs.
* Utilisez la solution de contournement suivante avec le code existant :

## Localisez `php.ini` {#locate-php-ini}

Recherchez `php.ini` en saisissant la commande suivante :

```php
php -i | grep "Loaded Configuration File"
```

Les emplacements types sont les suivants :

* Ubuntu : `/etc/php5/cli/php.ini`
* CentOS : `/etc/php.ini`

## Solution {#workaround}

1. En tant qu&#39;utilisateur disposant de droits `root`, ouvrez `php.ini` dans un éditeur de texte.
1. Localisez `session.save_handler`
1. Définissez-le de l’une des manières suivantes :
   * Pour le commenter :

     ```php
     ;session.save_path = <path>
     ```

   * Pour le définir sur un chemin d’accès au système de fichiers :

     ```php
     session.save_handler = files
     ```
