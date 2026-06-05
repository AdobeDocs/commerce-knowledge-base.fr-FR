---
title: Nouveaux environnements placés en production lorsqu’ils sont transférés depuis Git
description: Cet article fournit une solution au problème où de nouveaux environnements sont placés sous l’environnement de production sur Adobe Commerce sur l’infrastructure cloud lorsqu’ils sont poussés depuis le système de contrôle de version Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Nouveaux environnements placés en production lorsqu’ils sont transférés depuis Git

Cet article fournit une solution au problème où de nouveaux environnements sont placés sous l’environnement de production sur Adobe Commerce sur l’infrastructure cloud lorsqu’ils sont poussés depuis le système de contrôle de version Git.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

<u>Conditions préalables</u> :

disposer d’un clone local contrôlé par Git du projet ;

<u>Procédure à suivre </u> :

Vous devez créer une branche d’intégration à partir de la branche d’évaluation :

1. Basculez vers la branche d’évaluation en exécutant la commande suivante dans le shell local : `git checkout staging`
1. Créez une branche d’intégration à partir de la branche d’évaluation en exécutant la commande suivante dans le shell local : `git checkout -b <branch>`
1. Envoyez la branche au référentiel distant et configurez une branche en amont en exécutant la commande suivante dans le shell local : `git push --set-upstream origin <branch>`

<u>Résultats attendus</u> :

La nouvelle branche est créée sous la branche d’évaluation.

<u>Résultats réels</u> :

La nouvelle branche a été créée sous la branche de production .

## Cause

Ce n’est pas un bug. Pour définir une branche parent pour une autre branche, le commerçant doit utiliser l’interface de ligne de commande cloud magento.

## Solution

Une branche parent ne peut être définie qu’une fois que le commerçant a envoyé une branche nouvellement créée et l’a activée. Consultez [Adobe Commerce sur l’infrastructure cloud > Intégration de Bitbucket](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) dans notre documentation destinée aux développeurs.

Pour mettre à jour un parent pour la branche existante sur le serveur, utilisez la commande `magento-cloud environment:info` dans l’interface de ligne de commande magento-cloud.

Exemple d’utilisation :

`magento-cloud environment:info parent Staging`

Cette action définit la branche parent sur « Évaluation » pour la branche actuellement extraite.

## Lecture connexe

* [Adobe Commerce sur l’infrastructure cloud > Magento-cloud CLI](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) dans notre documentation destinée aux développeurs.
