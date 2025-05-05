---
title: Redirection vers un environnement parent lors de l’accès à un nouvel environnement d’intégration
description: Cet article fournit des instructions de dépannage pour Adobe Commerce sur le problème d’infrastructure cloud où la tentative d’accès à l’environnement d’intégration nouvellement créé vous conduit plutôt à l’environnement parent.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Redirection vers un environnement parent lors de l’accès à un nouvel environnement d’intégration

Cet article fournit des instructions de dépannage pour Adobe Commerce sur le problème d’infrastructure cloud où la tentative d’accès à l’environnement d’intégration nouvellement créé vous conduit plutôt à l’environnement parent.

Pour corriger ce problème, vous devez corriger la valeur base\_url dans la base de données et vous assurer que la valeur de variable `UPDATE_URLS` est définie sur `true`. Pour plus d’informations, reportez-vous aux sections ci-dessous.

Versions et éditions affectées :

* Adobe Commerce sur l’infrastructure cloud 2.X.X

## Problème

<u>Étapes à reproduire</u> :

1. Cloner la branche d’intégration existante.
1. Cliquez sur l&#39;URL d&#39;accès au nouvel environnement.

<u>Résultat attendu</u> :

Vous accédez à l’environnement nouvellement créé.

<u>Résultat réel</u> :

Vous êtes redirigé vers l’environnement sur la branche parente.

## Solution

Pour résoudre ce problème, vous devez corriger les valeurs `base_url` (sécurisées et non sécurisées) dans la base de données d’environnement personnalisée et définir la variable `UPDATE_URL` dans le fichier `.magento.env.yaml`.

### Correction des valeurs base\_url dans la base de données

Les modifications apportées à la base de données peuvent être effectuées manuellement ou à l’aide de l’interface de ligne de commande d’Adobe Commerce, si vous utilisez les versions 2.2.0 et ultérieures.

#### Corriger manuellement les valeurs dans la base de données.

1. Connexion à la base de données.
1. Exécutez les commandes suivantes :

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Corrigez la base de données à l’aide de l’interface de ligne de commande d’Adobe Commerce (disponible pour les versions 2.2.X).

1. Connectez-vous en tant que [propriétaire du système de fichiers Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html?lang=fr) ou basculez vers cet emplacement.
1. Exécutez les commandes suivantes :

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Définition de la variable `UPDATE_URLS`

Dans votre base de code locale, dans le jeu de fichiers `.magento.env.yaml` :

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Effacer le cache de configuration

Pour que les modifications soient appliquées, nettoyez le cache de configuration en exécutant la commande suivante :

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Article connexe dans notre documentation destinée aux développeurs :

[Déployer des variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=fr)
