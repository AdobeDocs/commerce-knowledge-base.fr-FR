---
title: Lors de l’installation, erreur Exception de reflet
description: Cet article fournit une solution à l’erreur Reflection Exception lors de l’installation.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Lors de l’installation, erreur Exception de reflet

Cet article fournit une solution à l’erreur Reflection Exception lors de l’installation.

## Détails {#details}

Pendant l’installation, un message similaire à celui-ci s’affiche :

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Solution {#solution}

Effacer tous les répertoires et fichiers sous Adobe Commerce `var` et réinstallez le logiciel Adobe Commerce.

Comme la variable [Propriétaire du système de fichiers Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) ou en tant qu’utilisateur avec `root` , saisissez les commandes suivantes :

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Si vous utilisez Redis et obtenez toujours une erreur, effacez le cache Redis comme suit :

```bash
$ redis-cli FLUSHALL
```
