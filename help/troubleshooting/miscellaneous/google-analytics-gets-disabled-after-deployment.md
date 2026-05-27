---
title: Google Analytics est désactivé après déploiement
description: Cette rubrique présente une solution à un problème type que vous pouvez rencontrer avec Google Analytics lors du déploiement.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Google Analytics est désactivé après déploiement

Cette rubrique présente une solution à un problème type que vous pouvez rencontrer avec Google Analytics lors du déploiement.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes versions confondues

## Problème

Lors du déploiement de votre code dans plusieurs environnements, les scripts de build et de déploiement vérifient que la branche `master/production/staging` est déployée pour conserver Google Analytics activé. Lors du déploiement de branches de développement (ou enfants) du maître vers les environnements de développement (intégration), le script de déploiement désactive Google Analytics.

## Cause

Il s’agit d’une fonctionnalité conçue pour s’assurer que les données et interactions des développeurs ne sont pas envoyées à ou suivies par Google Analytics.

## Solution

Si vous souhaitez que Google Analytics soit toujours activé, définissez le `ENABLE_GOOGLE_ANALYTICS = true` de variable de déploiement, comme décrit dans la section [Déployer les variables](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) de la documentation destinée aux développeurs.

>[!NOTE]
>
>Nous sommes conscients que cet article peut encore contenir des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressants et qui peuvent faire que le lecteur se sent blessé, traumatisé ou importun. Adobe s’efforce de supprimer ces termes de notre code, de notre documentation et de nos expériences utilisateur.
