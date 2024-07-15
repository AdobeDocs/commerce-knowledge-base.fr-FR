---
title: 'Erreur de déploiement : SQLSTATE[HY00]'
description: Cet article fournit une solution au problème d’échec du déploiement en raison de l’erreur SQLSTATE[HY000].
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Erreur de déploiement : SQLSTATE[HY000]

Cet article fournit une solution au problème d’échec du déploiement en raison de l’erreur SQLSTATE[HY000] .

## Produits et versions concernés

* Adobe Commerce, [toutes les méthodes de déploiement](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Une erreur SQLSTATE se produit lors du déploiement.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Cause

Cron s’exécutant pendant le déploiement.

## Solution

Pour résoudre ce problème, arrêtez l’exécution de cron en ouvrant la ligne de commande et en exécutant la commande suivante :
`./vendor/bin/ece-tools cron:disable`.
