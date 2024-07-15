---
title: Restriction de l’accès administrateur provoquant des problèmes de performances
description: Cet article fournit des solutions pour les cas où les performances sont affectées en utilisant [rôles d’administrateur avec portée de rôle limitée par le site web](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) dans notre guide d’utilisation.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Restriction de l’accès administrateur provoquant des problèmes de performances

Cet article fournit des solutions pour les cas où les performances sont affectées par l’utilisation de [rôles d’administrateur avec une portée de rôle limitée par le site web](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) dans notre guide d’utilisation.

## Produits et versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

Lorsqu’un utilisateur administrateur, dont la portée du rôle est limitée par le site web, effectue des opérations dans le panneau d’administration (notamment se connecter, enregistrer des produits, etc.), Adobe Commerce reconstruit le cache stocké. La reconstruction du cache a un impact négatif sur les performances et peut entraîner une panne du site, en particulier pendant les heures d’ouverture et/ou le trafic élevé.

Le problème est résolu dans Adobe Commerce 2.2.10 et 2.3.3.

## Solution

Vous trouverez ci-dessous les options permettant d’éviter le problème :

* Mettez à niveau la version de l’application Adobe Commerce vers 2.2.10 ou 2.3.3. (pour obtenir des instructions, reportez-vous à la section [Mise à niveau d’Adobe Commerce sur la version d’infrastructure cloud](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade.html) de notre documentation destinée aux développeurs).
* Si possible, évitez de limiter la portée du rôle d’utilisateur administrateur par site web.
* [Envoyez un ticket d’assistance Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander un correctif, s’il est disponible.

## Lecture connexe

* [Rôles utilisateur](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html) dans notre guide d’utilisation.
