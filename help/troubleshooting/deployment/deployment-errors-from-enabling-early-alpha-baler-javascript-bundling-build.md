---
title: Erreurs de déploiement à partir de l’activation du module d’Baler précoce alpha
description: Le marchand rencontre des erreurs de déploiement lors de l’utilisation du module Baler dans un environnement de production, car la fonctionnalité est actuellement en phase de développement alpha précoce.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Erreurs de déploiement à partir de l’activation du module d’Baler précoce alpha

Le marchand rencontre des erreurs de déploiement lors de l’utilisation du module Baler dans un environnement de production, car la fonctionnalité est actuellement en phase de développement alpha précoce.

>[!WARNING]
>
>Le regroupement JavaScript de Baler précoce n’est pas prêt à être utilisé en production et est utilisé à vos propres risques.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.x et 2.4.x.
* Adobe Commerce sur site 2.3.x et 2.4.x.

## Problème

Nous déconseillons aux commerçants d&#39;utiliser le module Baler dans un environnement de production, car il est actuellement en phase de développement de l&#39;alpha. Son utilisation peut entraîner des erreurs de déploiement.

<u>Étapes à reproduire</u> :

1. Le marchand tente d’insérer la variable **SCD\_USE\_BALER** dans l’étape de création du fichier `.magento.env.yaml`, ce qui active le package de bundling JavaScript Baler.
1. Le commerçant ajoute également la dépendance du compositeur Baler : `"magento/module-baler": "1.0.0-alpha"` à la section `require` de `composer.json`.

<u>Résultat attendu</u> :

Déploiement réussi.

<u>Résultat réel</u> :

Le marchand voit le message d’erreur suivant dans les journaux de déploiement sur le cloud, qui est `<project home>/var/log/cloud.log`, lors de l’étape de déploiement du contenu statique :

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Cause

Le module Baler est actuellement en phase de développement alpha précoce, et le processus d&#39;installation de l&#39;extension Baler est complexe.

## Solution

Vous pouvez consulter la documentation existante sur l’Alpha Baler à l’adresse [Github/Magento/Baler/Prise en main de l’alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Cependant, il n’est pas prêt à être utilisé en production et il est utilisé à vos risques et périls. Il est recommandé de fusionner ou de regrouper des fichiers JavaScript (JS) à l’aide d’Adobe Commerce en vue de l’optimisation des fichiers.

* Vous pouvez activer la fusion ou le regroupement dans l’administration (la fusion et le regroupement ne peuvent pas être activés en même temps) : **Magasins** > **Paramètres** > **Configuration** > **Avancé** > **Développeur** > **Paramètres JavaScript**.
* Vous pouvez également activer le regroupement intégré Adobe Commerce (regroupement de base) à partir de la ligne de commande : `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Pour en savoir plus, reportez-vous à la section [Optimisation des fichiers CSS et Javascript sur Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site](https://support.magento.com/hc/en-us/articles/360044482152).
