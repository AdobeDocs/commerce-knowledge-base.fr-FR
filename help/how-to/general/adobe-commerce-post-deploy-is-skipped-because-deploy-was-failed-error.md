---
title: Adobe Commerce *le post-déploiement est ignoré car le déploiement a échoué* erreur
description: 'Cet article explique comment rechercher une erreur de déploiement : *Post-deploy est ignoré car le déploiement a échoué*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *post-déploiement est ignoré car le déploiement a échoué* erreur

Cet article explique comment rechercher une erreur de déploiement : *Post-deploy est ignoré car le déploiement a échoué*, ce qui se produit lors du déploiement dans différents environnements, par exemple la mise à niveau.

## Produits et versions concernés

Adobe Commerce sur l&#39;infrastructure cloud [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Le déploiement échoue et renvoie un message d’erreur générique. Il n’est donc pas clair comment résoudre l’erreur.

## Cause

Indéterminé : ce qui provoque ce message d’erreur dépend du code et de la base de données déployés.

## Comment rechercher l’erreur de déploiement

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

Pour obtenir la trace de l&#39;erreur permettant de déterminer la cause réelle, SSH au serveur et vérifiez le fichier journal `var/log/install_upgrade.log`.
