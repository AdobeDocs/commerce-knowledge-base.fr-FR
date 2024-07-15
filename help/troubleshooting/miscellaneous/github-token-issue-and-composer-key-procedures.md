---
title: Problème de jeton Github et procédures clés du compositeur
description: Cet article fournit des solutions pour le problème des déploiements échoués liés aux échecs de jeton Github causés par des clés de compositeur obsolètes.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Problème de jeton Github et procédures clés du compositeur

Cet article fournit des solutions pour le problème des déploiements échoués liés aux échecs de jeton Github causés par des clés de compositeur obsolètes.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Compositeur versions 1.10.20 et antérieures

>[!NOTE]
>
>Les marchands sur site Adobe Commerce doivent vérifier auprès de leur fournisseur d’hôtes s’ils utilisent la version 1.10.21 ou ultérieure du compositeur en raison des modifications de format de jeton introduites par Git.

## Problème

Les déploiements échouent et les journaux de déploiement contiennent des informations similaires aux suivantes :

*Erreur fatale : Uncaught Uncaught UncaughtValueException : Your github oauth token for github.com contient des caractères non valides : &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot; dans /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Cause

Les clés du compositeur obsolètes provoquent des échecs de jeton Github qui entraînent l’échec des déploiements.

## Solution

Pour résoudre ce problème, mettez à jour votre version du compositeur vers la version 1.10.22 :

1. Sur votre environnement local, exécutez `composer require “composer/composer”:”>1.10.21`.
1. Cela ajoute la configuration requise pour cette version de module du compositeur. Vérifiez le fichier de verrouillage : la version `composer/composer` doit être 1.0.22 ou supérieure.
1. Validez `composer.json` et `composer.lock` et poussez un déploiement.

Si cette méthode ne fonctionne pas, [soumettez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lecture connexe

* [Blog Github : Derrière les nouveaux formats de jeton d’authentification de GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com article d’actualité : GitHub change le format de jeton pour améliorer l’identification, le numérisation secrète et l’entropie](https://www.infoq.com/news/2021/04/github-new-token-format/)
