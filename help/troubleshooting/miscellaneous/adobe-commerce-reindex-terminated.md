---
title: 'Adobe Commerce cloud : la réindexation s’arrête avec le message « Tué »'
description: '* Adobe Commerce sur les infrastructures cloud (toutes versions)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '235'
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

* [Architecture pro > Environnement d’intégration](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architecture de démarrage > Environnement d’évaluation](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
