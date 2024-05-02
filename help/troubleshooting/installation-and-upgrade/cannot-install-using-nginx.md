---
title: Impossible d’installer à l’aide de nginx
description: Cet article fournit un correctif pour une installation Adobe Commerce en échec lors de l’utilisation du serveur web nginx.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Impossible d’installer à l’aide de nginx

Cet article fournit un correctif pour une installation Adobe Commerce en échec lors de l’utilisation du serveur web nginx.

## Problème

Si vous utilisez le serveur web nginx et que vous tentez d’installer le logiciel Adobe Commerce, l’installation échoue parfois.

## Solution

Vous pouvez confirmer le problème en affichant l’erreur suivante dans la variable `var/report` directory:

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### Solution

Installez le logiciel Adobe Commerce à l’aide du [ligne de commande](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html).
