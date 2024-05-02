---
title: Problèmes connus qui affectent l’installation de xdebug
description: Cet article fournit une solution pour lorsque vous rencontrez une erreur d’exception lorsque vous utilisez l’extension PHP facultative "xdebug".
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Problèmes connus qui affectent l’installation de xdebug

Cet article fournit une solution pour lorsque vous rencontrez une erreur d’exception lorsque vous utilisez l’extension PHP facultative. `xdebug`.

* Pendant l’installation
* Accès à l’administrateur Commerce ou au storefront après une installation réussie

Exemple d’exception :

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Pour résoudre ce problème, vous pouvez :

* Désactivez la fonction `xdebug` extension .
* Définissez la valeur de `xdebug.max_nesting_level` sur une valeur de 200 ou plus. Pour plus d’informations, voir [documentation xdebug](http://xdebug.org/docs/basic#max_nesting_level).

Après avoir modifié la configuration de ou désactivé `xdebug`, redémarrez Apache :

* CentOS : `sudo service httpd restart`
* Ubuntu : `sudo service apache2 restart`
