---
title: Nouveaux environnements placés en production lorsqu’ils sont transférés depuis Git
description: Cet article fournit une solution au problème où de nouveaux environnements sont placés sous l’environnement de production sur Adobe Commerce sur l’infrastructure cloud lorsqu’ils sont poussés depuis le système de contrôle de version Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
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

Une branche parent ne peut être définie qu’une fois que le commerçant a envoyé une branche nouvellement créée et l’a activée. Consultez [Adobe Commerce sur l’infrastructure cloud > Intégration de Bitbucket](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) dans notre documentation destinée aux développeurs.

Pour mettre à jour un parent pour la branche existante sur le serveur, utilisez la commande `magento-cloud environment:info` dans l’interface de ligne de commande magento-cloud.

Exemple d’utilisation :

`magento-cloud environment:info parent Staging`

Cette action définit la branche parent sur « Évaluation » pour la branche actuellement extraite.

## Lecture connexe

* [Adobe Commerce sur l’infrastructure cloud > Magento-cloud CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) dans notre documentation destinée aux développeurs.
