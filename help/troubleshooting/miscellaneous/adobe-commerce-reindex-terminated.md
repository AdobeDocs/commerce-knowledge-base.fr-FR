---
title: '"Cloud Adobe Commerce : la réindexation est arrêtée avec le message "Tué"'
description: '* Adobe Commerce sur l’infrastructure cloud (toutes versions)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Cloud Adobe Commerce : la réindexation est arrêtée avec le message `Killed`

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Vous tentez d’exécuter une réindexation sur la branche d’intégration (ou sur l’évaluation du projet d’architecture Starter), et le processus est arrêté avec le message `Killed`.

## Cause

Cela se produit généralement parce que les processus PHP manquent de mémoire.
La raison la plus courante est un grand nombre de produits, magasins et/ou groupes de clients sur l’instance.

## Solution

1. Réduire le nombre de produits (ainsi que les groupes de clients et les magasins, le cas échéant).
1. Limitez l’utilisation à un ou deux utilisateurs simultanés.
1. Désactivez les tâches cron et exécutez-les manuellement si nécessaire.
1. Si cela n’a pas été fait précédemment, demandez une mise à niveau vers les environnements d’intégration améliorée. Notez la restriction quant au nombre d’environnements auxquels vous seriez limité une fois la mise à niveau effectuée. Pour plus d’informations, reportez-vous à l’article [Demande d’amélioration de l’environnement d’intégration - Pro et Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) dans notre base de connaissances de prise en charge.

## Lecture connexe :

Dans notre documentation destinée aux développeurs :

* [Architecture Pro > Environnement d’intégration](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [Architecture de démarrage > Environnement d’évaluation](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
