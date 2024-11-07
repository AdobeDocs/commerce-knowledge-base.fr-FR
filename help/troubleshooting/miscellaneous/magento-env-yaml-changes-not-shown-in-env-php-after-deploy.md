---
title: Les modifications .magento.env.yaml ne s’affichent pas dans env.php après le déploiement
description: Cet article fournit une solution au problème où les modifications du fichier .magento.env.yaml ne sont pas répercutées dans app/etc/env.php après le déploiement.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Les modifications .magento.env.yaml ne s’affichent pas dans env.php après le déploiement

>[!NOTE]
>
>Si vous rencontrez ce problème, effectuez une mise à niveau vers les outils de la version 2002.1.5 pour le résoudre. La version 2002.1.5 dispose d’une fonctionnalité permettant de réinitialiser l’opcache sur chaque déploiement. Il n’est donc jamais nécessaire de modifier le paramètre `opcache.enable_cli=1`. Si vous ne souhaitez pas effectuer de mise à niveau, vous devez suivre les étapes de contournement décrites ci-dessous dans la solution.

Cet article fournit une solution au problème où les modifications du fichier `.magento.env.yaml` ne sont pas répercutées dans `app/etc/env.php` après le déploiement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problème

Les modifications effectuées dans le fichier `.magento.env.yaml` n’affectent pas le `app/etc/env.php` généré.

<u>Étapes à reproduire :</u>

Modifiez toute valeur de `.magento.env.yaml` et envoyez-la au serveur, où il doit définir la configuration (et les paramètres de déploiement) de l’environnement actuellement extrait. Pour les étapes, voir [Variables d’environnement > Déployer des variables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) dans notre documentation destinée aux développeurs.

<u>Résultat attendu :</u>

Les modifications effectuées dans le fichier `.magento.env.yaml` affectent les `app/etc/env.php` générés.

<u>Résultat réel :</u>

Les modifications n’ont aucun effet sur les variables `app/etc/env.php` après le déploiement.

## Cause

Le problème peut être dû à une valeur incorrecte du paramètre `opcache.enable_cli` dans le fichier `php.ini`.

## Solution

1. Vérifiez que le système est configuré conformément aux [Bonnes pratiques de performances d’Adobe Commerce > Recommandations logicielles](https://experienceleague.adobe.com/en/docs/commerce-operations/performance-best-practices/software).
1. Vérifiez si la directive `opcache.enable_cli` de `php.ini` est définie sur `0` en exécutant : `php -i | grep opcache.enable_cli`
1. Si la sortie ressemble à `opcache.enable_cli=1` , modifiez le fichier `php.ini` dans le répertoire racine du projet et remplacez `opcache.enable_cli=1` par `opcache.enable_cli=0`.
1. Redéployez le projet.

## Lecture connexe

* [Cloud pour Adobe Commerce > Créer et déployer](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml).
