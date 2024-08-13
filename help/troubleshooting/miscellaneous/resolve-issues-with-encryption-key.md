---
title: Résolution de problèmes liés à la clé de chiffrement
description: Cet article explique comment résoudre les problèmes causés par le déplacement de la clé de chiffrement avec le vidage DB vers l’autre environnement.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Résolution de problèmes liés à la clé de chiffrement

Cet article explique comment résoudre les problèmes causés par le déplacement de la clé de chiffrement avec le vidage DB vers l’autre environnement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.x

## Problème

Après avoir importé un [vidage de base de données](/help/how-to/general/create-database-dump-on-cloud.md) de l’environnement de production vers l’environnement d’évaluation/d’intégration, les numéros de carte de crédit enregistrés apparaissent incorrects et/ou les paiements échouent pour les intégrations de paiement nécessitant l’utilisation des informations d’identification du commerçant.

## Cause

La clé de cryptage utilisée pour crypter des données sensibles, telles que les numéros de carte de crédit et les informations d’identification du commerçant, n’est pas stockée dans la base de données et n’est donc pas transférée vers un autre environnement après l’importation/exportation de la base de données.

## Solution

Vous devez copier la clé de chiffrement de l’environnement source et l’ajouter à l’environnement de destination.

Pour copier la clé de chiffrement :

1. SSH à votre projet qui était la source du vidage de la base de données, comme décrit dans [SSH to environment](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) dans notre documentation destinée aux développeurs.
1. Ouvrez `app/etc/env.php` dans un éditeur de texte.
1. Copiez la valeur de `key` pour `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Pour définir la valeur clé du projet de destination :

1. Ouvrez la [console cloud](https://console.adobecommerce.com) et localisez votre projet.
1. Définissez la valeur de la variable [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (dans notre documentation destinée aux développeurs), comme décrit dans la section [Configuration de votre projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) de notre documentation destinée aux développeurs. Cela déclenchera le processus de déploiement et `CRYPT_KEY` sera remplacé dans le fichier `app/etc/env.php` sur chaque déploiement.

Vous pouvez éventuellement remplacer manuellement la clé de chiffrement dans le fichier `app/etc/env.php` :

1. SSH vers l’environnement de destination.
1. Ouvrez `app/etc/env.php` dans un éditeur de texte.
1. Collez les données copiées en tant que valeur `key` pour `crypt`.
1. Enregistrez le `env.php` modifié.
1. Nettoyez le cache sur l’environnement de destination en exécutant `bin/magento cache:clean` ou dans l’administrateur Commerce sous **System** > **Tools** > **Cache Management**.
