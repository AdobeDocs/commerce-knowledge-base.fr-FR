---
title: Les Google Analytics sont désactivés après le déploiement
description: Cette rubrique aborde une solution à un problème typique que vous pouvez rencontrer avec des Google Analytics pendant le déploiement.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Les Google Analytics sont désactivés après le déploiement

Cette rubrique aborde une solution à un problème typique que vous pouvez rencontrer avec des Google Analytics pendant le déploiement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

Lors du déploiement de votre code dans plusieurs environnements, les scripts de création et de déploiement vérifient que la branche `master/production/staging` est déployée pour que les Google Analytics restent activés. Lors du déploiement de branches de développement (ou enfants) de maître dans des environnements de développement (intégration), le script de déploiement désactive les Google Analytics.

## Cause

Il s’agit d’une fonctionnalité prévue pour s’assurer que les données et interactions des développeurs ne sont pas envoyées ou suivies par les Google Analytics.

## Solution

Si vous souhaitez que les Google Analytics soient toujours activés, définissez la variable de déploiement `ENABLE_GOOGLE_ANALYTICS = true`, comme décrit dans la section [Déployer des variables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) de notre documentation destinée aux développeurs.

>[!NOTE]
>
>Nous sommes conscients que cet article peut encore contenir des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.
