---
title: 'Adobe Commerce cloud : la réindexation s’arrête avec le message « Tué »'
description: '* Adobe Commerce sur les infrastructures cloud (toutes versions)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Adobe Commerce cloud : la réindexation se termine par `Killed` message

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud (toutes versions)

## Problème

Vous essayez d’exécuter une réindexation sur la branche Intégration (ou sur l’évaluation du projet d’architecture de démarrage) et le processus est en cours d’arrêt avec le message `Killed` .

## Cause

Cela se produit généralement parce que les processus PHP manquent de mémoire.
La raison la plus courante est un grand nombre de produits, de magasins et/ou de groupes de clients sur l’instance .

## Solution

1. Réduisez le nombre de produits (ainsi que le nombre de groupes de clients et de magasins, le cas échéant).
1. Limitez l’utilisation à un ou deux utilisateurs simultanés.
1. Désactivez les tâches cron et exécutez-les manuellement selon vos besoins.
1. Si cela n’a pas été fait auparavant, demandez une mise à niveau vers les environnements d’intégration améliorée - prenez note de la restriction du nombre d’environnements auxquels vous seriez limité une fois la mise à niveau effectuée. Pour plus d’informations, consultez l’article [&#x200B; Demande d’amélioration de l’environnement d’intégration - Pro et Starter &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27242) dans notre base de connaissances d’assistance.

## Lecture connexe :

Dans notre documentation destinée aux développeurs :

* [Architecture Pro > Environnement d’intégration](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architecture de démarrage > Environnement d’évaluation](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
