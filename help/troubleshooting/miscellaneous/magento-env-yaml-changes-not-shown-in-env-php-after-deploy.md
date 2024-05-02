---
title: Les modifications .magento.env.yaml ne s’affichent pas dans env.php après le déploiement
description: Cet article fournit une solution au problème où les modifications du fichier .magento.env.yaml ne sont pas répercutées dans app/etc/env.php après le déploiement.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Les modifications .magento.env.yaml ne s’affichent pas dans env.php après le déploiement

>[!NOTE]
>
>Si vous rencontrez ce problème, effectuez une mise à niveau vers les outils de la version 2002.1.5 pour le résoudre. La version 2002.1.5 dispose d’une fonctionnalité permettant de réinitialiser l’opcache sur chaque déploiement. Il n’est donc jamais nécessaire de modifier le paramètre `opcache.enable_cli=1`. Si vous ne souhaitez pas effectuer de mise à niveau, vous devez suivre les étapes de contournement décrites ci-dessous dans la solution.

Cet article fournit une solution au problème où les modifications dans `.magento.env.yaml` n’est pas reflété dans `app/etc/env.php` après le déploiement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problème

Modifications apportées dans la variable `.magento.env.yaml` n’affectent pas le fichier `app/etc/env.php` généré.

<u>Étapes à reproduire :</u>

Modifier une valeur dans `.magento.env.yaml` et push vers le serveur, où il doit définir la configuration (et les paramètres de déploiement) de l’environnement actuellement extrait. Pour connaître les étapes, voir [Variables d’environnement > Déployer des variables](https://devdocs.magento.com/cloud/env/variables-deploy.html) dans notre documentation destinée aux développeurs.

<u>Résultat attendu :</u>

Modifications apportées dans la variable `.magento.env.yaml` affecte le fichier `app/etc/env.php` généré.

<u>Résultat réel :</u>

Les modifications n’ont aucun effet sur la variable `app/etc/env.php` après le déploiement.

## Cause

Le problème peut être dû à une valeur incorrecte de la variable `opcache.enable_cli` du paramètre `php.ini` fichier .

## Solution

1. Vérifiez que le système est configuré selon les [Bonnes pratiques de performances d’Adobe Commerce > Recommandations logicielles](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Vérifier si `opcache.enable_cli` directive dans `php.ini` est défini sur `0` en exécutant : `php -i | grep opcache.enable_cli`
1. Si la sortie ressemble à `opcache.enable_cli=1` , modifiez la variable `php.ini` dans le répertoire racine du projet et modifiez `opcache.enable_cli=1` to `opcache.enable_cli=0`
1. Redéployez le projet.

## Lecture connexe

* [Cloud pour Adobe Commerce > Créer et déployer](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
