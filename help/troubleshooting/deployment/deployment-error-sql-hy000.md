---
title: 'Erreur de déploiement : SQLSTATE[HY000]'
description: Cet article fournit une solution au problème d’échec du déploiement en raison de l’erreur SQLSTATE[HY000].
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 5%
---
# Erreur de déploiement : SQLSTATE[]

Cet article fournit une solution au problème d&#39;échec du déploiement en raison de l&#39;erreur SQLSTATE[].

## Produits et versions concernés

* Adobe Commerce, [toutes les méthodes de déploiement](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Une erreur SQLSTATE se produit lors du déploiement.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Cause

Cron en cours d’exécution lors du déploiement.

## Solution

Pour résoudre ce problème, arrêtez l’exécution de cron en ouvrant la ligne de commande et en exécutant la commande suivante :
`./vendor/bin/ece-tools cron:disable`.
