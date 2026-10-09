---
title: exécutez le problème « setup:static-content:deploy » deploy_version.txt .
description: Cet article fournit un correctif pour l’erreur « deploy_version.txt » n’est pas accessible en écriture lors de l’exécution manuelle de la commande « setup:static-content:deploy ».
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%
---
# exécuter `setup:static-content:deploy` problème deploy_version.txt

Cet article fournit un correctif pour l’erreur `deployed_version.txt` n’est pas accessible en écriture lors de l’exécution manuelle de la commande `setup:static-content:deploy`.

## Problème

Si vous suivez les recommandations d’Adobe Commerce sur l’infrastructure cloud pour utiliser la gestion de la configuration (et déplacez la génération des ressources statiques vers l’étape de création afin de réduire le temps d’arrêt du site web lors du déploiement), vous pouvez rencontrer l’erreur suivante lors de l’exécution manuelle de la commande `setup:static-content:deploy` :

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Cause

Nous avons optimisé le processus de déploiement pour réduire les temps d’arrêt et créé des liens symboliques vers des fichiers de ressources statiques au lieu de les copier. L’emplacement de stockage des ressources statiques est en lecture seule, c’est pourquoi vous recevez le message d’erreur ci-dessus.

Il est vivement déconseillé d’exécuter le déploiement de contenu statique manuellement, car toutes les ressources sont déjà générées et il n’y aura aucune différence entre les fichiers si vous le faites manuellement (les fichiers de thème sont également en lecture seule, vous ne pouvez pas les modifier). Cette opération n’a donc aucun sens.

## Solution

Si vous souhaitez toujours exécuter le déploiement de contenu statique, supprimez les liens symboliques du répertoire `pub/static` et exécutez à nouveau la commande `setup:static-content:deploy` :

```
find pub/static/ -maxdepth 1 -type l -delete
```
