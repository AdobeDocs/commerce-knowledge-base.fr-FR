---
title: L’installation s’arrête à environ 70 %
description: Cet article fournit un correctif pour le moment où l’installation s’arrête à environ 70 %.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# L’installation s’arrête à environ 70 %

Cet article fournit un correctif pour le moment où l’installation s’arrête à environ 70 %.

## Problème

Lors de l’installation à l’aide de l’assistant d’installation, le processus s’arrête à environ 70 % (avec ou sans données d’exemple). Aucune erreur ne s’affiche à l’écran.

## Cause

Les causes courantes de ce problème incluent :

* Le paramètre PHP pour [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Valeurs de délai d’expiration pour les onglets et le vernis

## Solution :

Définissez toutes les options suivantes selon vos besoins.

### Tous les serveurs web et Vernis {#all-web-servers-and-varnish}

1. Localisez votre `php.ini` à l’aide d’un fichier [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. En tant qu’utilisateur disposant de droits d’`root`, ouvrez `php.ini` dans un éditeur de texte.
1. Recherchez le paramètre `max_execution_time` .
1. Remplacez sa valeur par `18000` .
1. Enregistrez vos modifications dans `php.ini` et quittez l’éditeur de texte.
1. Redémarrez Apache :

   * CentOS : `service httpd restart`
   * Ubuntu : `service apache2 restart`

   Si vous utilisez Nginx ou Varnish, continuez avec les sections suivantes.

### nginx uniquement {#nginx-only}

Si vous utilisez nginx, utilisez le `nginx.conf.sample` inclus ou ajoutez un paramètre de délai d&#39;expiration dans le fichier de configuration de l&#39;hôte nginx à la section `location ~ ^/setup/index.php` comme suit :

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Redémarrez nginx : `service nginx restart`

### Vernis uniquement {#varnish-only}

Si vous utilisez le vernis, modifiez la `default.vcl` et ajoutez une valeur de limite de délai d’expiration à la strate de `backend` comme suit :

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
