---
title: Restriction de l’accès administrateur provoquant des problèmes de performances
description: Cet article fournit des solutions pour les cas où les performances sont affectées en utilisant [rôles d’administrateur avec portée de rôle limitée par le site web](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) dans notre guide d’utilisation.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Restriction de l’accès administrateur provoquant des problèmes de performances

Cet article fournit des solutions pour les cas où les performances sont affectées par l’utilisation de [rôles d’administrateur avec une portée de rôle limitée par le site web](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) dans notre guide d’utilisation.

## Produits et versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x

## Problème

Lorsqu’un utilisateur administrateur, dont la portée du rôle est limitée par le site web, effectue des opérations dans le panneau d’administration (notamment se connecter, enregistrer des produits, etc.), Adobe Commerce reconstruit le cache stocké. La reconstruction du cache a un impact négatif sur les performances et peut entraîner une panne du site, en particulier pendant les heures d’ouverture et/ou le trafic élevé.

Le problème est résolu dans Adobe Commerce 2.2.10 et 2.3.3.

## Solution

Vous trouverez ci-dessous les options permettant d’éviter le problème :

* Mettez à niveau la version de l’application Adobe Commerce vers 2.2.10 ou 2.3.3. (pour obtenir des instructions, reportez-vous à la section [Mise à niveau d’Adobe Commerce sur la version d’infrastructure cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) de notre documentation destinée aux développeurs).
* Si possible, évitez de limiter la portée du rôle d’utilisateur administrateur par site web.
* [Envoyez un ticket d’assistance Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander un correctif, s’il est disponible.

## Lecture connexe

* [Rôles utilisateur](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) dans notre guide d’utilisation.
