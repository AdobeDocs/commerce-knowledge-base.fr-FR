---
title: Lors de l’installation, une erreur PDO irrécupérable s’affiche.
description: Cet article fournit un correctif pour une erreur PDO fatale d’exception lors de l’installation.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Lors de l’installation, une erreur PDO irrécupérable s’affiche.

Cet article fournit un correctif pour une erreur PDO fatale d’exception lors de l’installation.

## Problème

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Solution

Assurez-vous d’installer toutes les [extensions PHP requises](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/php-settings).
