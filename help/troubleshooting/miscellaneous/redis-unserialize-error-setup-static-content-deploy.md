---
title: Redis unserialize error `setup:static-content:deploy
description: Cet article fournit un correctif pour l’erreur Redis unserialize lors de l’exécution de la configuration `magento:static-content:deploy`.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis unserialize error `setup:static-content:deploy`

Cet article fournit un correctif pour l’erreur Redis unserialize lors de l’exécution de `magento setup:static-content:deploy`.

En cours `magento setup:static-content:deploy` provoque l’erreur Redis :

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Le problème est dû à des processus d’interférence parallèles sur la connexion Redis.

Pour résoudre, exécutez `setup:static-content:deploy` dans un mode de thread unique en définissant la variable d’environnement suivante :

```
STATIC_CONTENT_THREADS =1
```

ou, exécutez le `setup:static-content:deploy` suivi de la commande `-j 1` (ou `--jobs=1` ).

Notez que la désactivation du multi-thread ralentit le processus de déploiement des ressources statiques.

## Versions affectées

* Adobe Commerce sur site : 2.1.2 et versions ultérieures
* Adobe Commerce sur l’infrastructure cloud 2.1.2 et versions ultérieures
* Redis, toute version

## Problème

Exécutez la variable `setup:static-content:deploy` entraîne l’erreur Redis :

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Cause

Le problème est dû à des processus d’interférence parallèles sur la connexion Redis.

Ici, un processus dans `App/Config/Type/System.php` attendait une réponse pour `system_defaultweb`, mais a reçu une réponse pour `system_cache_exists` cela a été fait par un processus différent. Consultez l’explication détaillée à la section [Article de Jason Woods](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Solution

Désactiver le parallélisme et exécuter `setup:static-content:deploy` dans un mode de thread unique en définissant la variable d’environnement suivante :

```
STATIC_CONTENT_THREADS =1
```

Vous pouvez également exécuter la fonction `setup:static-content:deploy` suivi de la commande `-j 1` (ou `--jobs=1`).

>[!NOTE]
>
>En mode thread unique, le processus de déploiement du contenu statique peut prendre quatre fois plus de temps.

## Informations supplémentaires

Dans notre documentation destinée aux développeurs :

* [Configuration de Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Mise à niveau de ligne de commande](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
