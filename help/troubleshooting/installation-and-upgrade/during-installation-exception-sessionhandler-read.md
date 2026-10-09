---
title: Lors de l’installation, exception SessionHandler::read()
description: Cet article fournit un correctif pour une erreur d’exception **SessionHandler::read()** lors de l’installation d’Adobe Commerce.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%
---

# Lors de l’installation, exception SessionHandler::read()

Cet article fournit un correctif pour une erreur d’exception **SessionHandler::read()** lors de l’installation d’Adobe Commerce.

## Problème

À la dernière étape de l’installation d’Adobe Commerce, l’exception suivante s’affiche :

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Cette erreur se produit uniquement dans les versions de code antérieures au 28 septembre 2015. Si vous installez du code daté du 29 septembre ou d’une date ultérieure, cette erreur ne devrait pas se produire. Pour plus d’informations sur les options de configuration de Redis, consultez [Configurer Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) dans notre documentation destinée aux développeurs. Pour plus d’informations sur la spécification de Redis à l’aide du programme d’installation de ligne de commande, consultez la [rubrique d’installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) ou la [rubrique de configuration du déploiement](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment) dans notre documentation destinée aux développeurs.

## Cause

Cela se produit lorsque votre paramètre PHP `session.save_handler` est défini sur un autre stockage de session que `files` (par exemple, `redis`, `memcached`, etc.). Il s’agit d’un problème connu que nous nous efforçons de résoudre.

## Solutions :

* Mettez à niveau votre code Adobe Commerce. Consultez [&#x200B; Guide d’installation > Mise à jour du logiciel Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall) dans notre documentation destinée aux développeurs.
* Utilisez la solution suivante avec le code existant :

## Localiser `php.ini` {#locate-php-ini}

Localisez `php.ini` en saisissant la commande suivante :

```php
php -i | grep "Loaded Configuration File"
```

Voici des emplacements standard :

* Ubuntu : `/etc/php5/cli/php.ini`
* CentOS : `/etc/php.ini`

## Solution {#workaround}

1. En tant qu’utilisateur disposant de droits d’`root`, ouvrez `php.ini` dans un éditeur de texte.
1. Localiser `session.save_handler`
1. Définissez-le de l’une des manières suivantes :
   * Pour le commenter :

     ```php
     ;session.save_path = <path>
     ```

   * Pour le définir sur un chemin d’accès au système de fichiers :

     ```php
     session.save_handler = files
     ```
