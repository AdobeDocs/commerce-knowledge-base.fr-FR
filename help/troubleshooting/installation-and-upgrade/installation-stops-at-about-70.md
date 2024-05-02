---
title: L’installation s’arrête à environ 70 %
description: Cet article fournit un correctif pour lorsque l’installation s’arrête à environ 70 %.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# L’installation s’arrête à environ 70 %

Cet article fournit un correctif pour lorsque l’installation s’arrête à environ 70 %.

## Problème

Lors de l’installation à l’aide de l’assistant de configuration, le processus s’arrête à environ 70 % (avec ou sans données d’exemple). Aucune erreur ne s’affiche à l’écran.

## Cause

Causes possibles de ce problème :

* Le paramètre PHP pour [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Valeurs de délai d’expiration de ingx et de vernis

## Solution :

Définissez tous les éléments suivants selon les besoins.

### Tous les serveurs web et vernis {#all-web-servers-and-varnish}

1. Recherchez votre `php.ini` en utilisant une [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) fichier .
1. En tant qu’utilisateur avec `root` privilèges, ouvrir `php.ini` dans un éditeur de texte.
1. Recherchez la variable `max_execution_time` .
1. Remplacez sa valeur par `18000` .
1. Enregistrez vos modifications dans `php.ini` et quittez l’éditeur de texte.
1. Redémarrez Apache :

   * CentOS : `service httpd restart`
   * Ubuntu : `service apache2 restart`

   Si vous utilisez le signe ou le vernis, passez aux sections suivantes.

### nginx uniquement {#nginx-only}

Si vous utilisez nginx, utilisez notre `nginx.conf.sample` ou ajoutez un paramètre d’expiration dans le fichier de configuration de l’hôte nginx au `location ~ ^/setup/index.php` , comme suit :

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Redémarrez le nginx : `service nginx restart`

### Uniquement en vernis {#varnish-only}

Si vous utilisez le vernis, modifiez les `default.vcl` et ajoutez une valeur limite de délai d’expiration à la variable `backend` stanza :

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Redémarrez le vernis.

```php
service varnish restart
```
