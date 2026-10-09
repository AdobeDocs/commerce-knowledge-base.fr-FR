---
title: Lors de l'installation, Erreur d'exception de réflexion
description: Cet article fournit une solution pour l'erreur d'exception de réflexion lors de l'installation.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
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
source-wordcount: '107'
ht-degree: 0%
---
# Lors de l&#39;installation, Erreur d&#39;exception de réflexion

Cet article fournit une solution pour l&#39;erreur d&#39;exception de réflexion lors de l&#39;installation.

## Détails {#details}

Lors de l’installation, un message similaire au suivant s’affiche :

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Solution {#solution}

Effacez tous les répertoires et fichiers du sous-répertoire `var` d’Adobe Commerce et réinstallez le logiciel Adobe Commerce.

En tant que propriétaire du système de fichiers Adobe Commerce [&#128279;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) ou en tant qu&#39;utilisateur disposant de privilèges `root`, saisissez les commandes suivantes :

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Si vous utilisez Redis et que vous obtenez toujours une erreur, effacez le cache Redis comme suit :

```bash
$ redis-cli FLUSHALL
```
