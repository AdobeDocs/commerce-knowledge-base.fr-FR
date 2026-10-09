---
title: Problèmes connus affectant l’installation de xdebug
description: Cet article fournit une solution lorsque vous rencontrez une erreur d’exception lorsque vous utilisez l’extension PHP facultative « xdebug ».
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# Problèmes connus affectant l’installation de xdebug

Cet article fournit une solution lorsque vous rencontrez une erreur d&#39;exception lorsque vous utilisez l&#39;extension PHP facultative `xdebug`.

* Pendant l’installation
* Accès à Commerce Admin ou à Storefront après une installation réussie

Exemple d’exception :

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Pour résoudre ce problème, vous pouvez :

* Désactivez l’extension `xdebug`.
* Définissez la valeur de `xdebug.max_nesting_level` sur une valeur de 200 ou plus. Pour plus d’informations, voir [documentation xdebug](http://xdebug.org/docs/basic#max_nesting_level).

Après avoir modifié la configuration de ou désactivé `xdebug`, redémarrez Apache :

* CentOS : `sudo service httpd restart`
* Ubuntu : `sudo service apache2 restart`
