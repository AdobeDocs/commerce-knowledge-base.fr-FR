---
title: exécutez le problème « setup:static-content:deploy » du fichier deploy_version.txt .
description: Cet article fournit un correctif pour l’erreur « deploy_version.txt » n’est pas accessible en écriture lors de l’exécution manuelle de la commande « setup:static-content:deploy ».
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: d7c714cf5b2f9db139440d814af26c12001bb4d9
workflow-type: tm+mt
source-wordcount: '193'
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
