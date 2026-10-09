---
title: Problème de jeton Github et procédures clés du compositeur
description: Cet article fournit des solutions au problème des échecs de déploiement liés aux échecs des jetons Github causés par des clés de compositeur obsolètes.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 23bc8570-95c6-5ef5-a563-2e4a4e6b4853
    internal-label: Identity Management
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# Problème de jeton Github et procédures clés du compositeur

Cet article fournit des solutions au problème des échecs de déploiement liés aux échecs des jetons Github causés par des clés de compositeur obsolètes.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Compositeur versions 1.10.20 et antérieures

>[!NOTE]
>
>Les commerçants sur site Adobe Commerce doivent vérifier auprès de leur fournisseur hôte qu’ils utilisent le compositeur version 1.10.21 ou ultérieure en raison des modifications du format de jeton introduites par Git.

## Problème

Les déploiements échouent et les journaux de déploiement contiennent des informations similaires à ce qui suit :

*Erreur fatale : Uncaught UnexpectedValueException : votre jeton oauth github pour github.com contient des caractères non valides : « ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx » dans /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Cause

Les clés de compositeur obsolètes entraînent des échecs de jeton Github, ce qui entraîne des échecs de déploiement.

## Solution

Pour résoudre le problème, veuillez mettre à jour votre compositeur vers la version 1.10.22 :

1. Sur votre environnement local, exécutez `composer require “composer/composer”:”>1.10.21`.
1. Cela ajoute l’exigence de cette version du package du compositeur. Vérifiez le fichier de verrouillage. `composer/composer` version doit être 1.0.22 ou une version ultérieure.
1. Validez le `composer.json` et le `composer.lock`, puis envoyez un déploiement .

Si cette méthode ne fonctionne pas, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

## Lecture connexe

* [Blog Github : derrière les nouveaux formats de jeton d’authentification de GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com : GitHub modifie le format des jetons pour améliorer l’identifiabilité, l’analyse secrète et l’entropie](https://www.infoq.com/news/2021/04/github-new-token-format/)
