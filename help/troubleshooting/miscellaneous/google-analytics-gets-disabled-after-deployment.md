---
title: Google Analytics est désactivé après déploiement
description: Cette rubrique présente une solution à un problème type que vous pouvez rencontrer avec Google Analytics lors du déploiement.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
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
