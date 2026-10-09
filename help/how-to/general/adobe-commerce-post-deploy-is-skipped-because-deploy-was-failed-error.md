---
title: Adobe Commerce *le post-déploiement est ignoré, car le déploiement a échoué*
description: 'Cet article explique comment rechercher une erreur de déploiement : *Le post-déploiement est ignoré, car le déploiement a échoué*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%
---
# Adobe Commerce *le post-déploiement est ignoré, car le déploiement a échoué* erreur

Cet article explique comment rechercher une erreur de déploiement : *Le post-déploiement est ignoré, car le déploiement a échoué* ce qui se produit lors du déploiement dans différents environnements, par exemple la mise à niveau.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Le déploiement échoue et renvoie un message d’erreur générique. La manière de résoudre l’erreur n’est donc pas claire.

## Cause

Indéterminé : la cause de ce message d’erreur dépend du code et de la base de données déployés.

## Comment examiner l’erreur de déploiement

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Pour obtenir la trace de l’erreur afin de déterminer la cause réelle, envoyez SSH au serveur et vérifiez le fichier journal `var/log/install_upgrade.log`.
