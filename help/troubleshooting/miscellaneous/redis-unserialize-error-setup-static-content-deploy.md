---
title: Redis unserialize error &grave;setup:static-content:deploy&grave;
description: Cet article fournit un correctif pour l’erreur Redis unserialize lors de l’exécution de &grave;magento setup:static-content:deploy&grave;.
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

L&#39;exécution de `magento setup:static-content:deploy` provoque l&#39;erreur Redis :

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Le problème est dû à des processus d’interférence parallèles sur la connexion Redis.

Pour résoudre ce problème, exécutez `setup:static-content:deploy` en mode de thread unique en définissant la variable d&#39;environnement suivante :

```
STATIC_CONTENT_THREADS =1
```

ou exécutez la commande `setup:static-content:deploy` suivie de l’argument `-j 1` (ou `--jobs=1` ).

Notez que la désactivation du multi-thread ralentit le processus de déploiement des ressources statiques.

## Versions affectées

* Adobe Commerce sur site : 2.1.2 et versions ultérieures
* Adobe Commerce sur l’infrastructure cloud 2.1.2 et versions ultérieures
* Redis, toute version

## Problème

L&#39;exécution de la commande `setup:static-content:deploy` provoque l&#39;erreur Redis :

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

Ici, un processus dans `App/Config/Type/System.php` attendait une réponse pour `system_defaultweb`, mais a reçu une réponse pour `system_cache_exists` qui a été effectuée par un autre processus. Consultez l’explication détaillée dans la [publication de Jason Woods](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Solution

Désactivez le parallélisme et exécutez `setup:static-content:deploy` en mode mono-thread en définissant la variable d&#39;environnement suivante :

```
STATIC_CONTENT_THREADS =1
```

Vous pouvez également exécuter la commande `setup:static-content:deploy` suivie de l’argument `-j 1` (ou `--jobs=1`).

>[!NOTE]
>
>En mode thread unique, le processus de déploiement du contenu statique peut prendre quatre fois plus de temps.

## Informations supplémentaires

Dans notre documentation destinée aux développeurs :

* [Configurer Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Mise à niveau de ligne de commande](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
