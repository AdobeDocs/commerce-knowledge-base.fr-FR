---
title: Problème run &grave;setup:static-content:deploy_version.txt
description: Cet article fournit un correctif pour &grave;deploy_version.txt&grave; n’est pas une erreur en écriture lors de l’exécution manuelle de la commande &grave;setup:static-content:deploy&grave;.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Problème run `setup:static-content:deploy` deploy_version.txt

Cet article fournit un correctif pour `deployed_version.txt` ne peut pas être écrit en erreur lors de l’exécution manuelle de la commande `setup:static-content:deploy`.

## Problème

Si vous suivez les recommandations d’infrastructure de cloud d’Adobe Commerce pour utiliser [Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (et déplacez la génération de ressources statiques à l’étape de création afin de réduire le temps d’arrêt du site web lors du déploiement), vous pouvez rencontrer l’erreur suivante lors de l’exécution manuelle de la commande `setup:static-content:deploy` :

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

Il est vivement déconseillé d’exécuter manuellement le déploiement de contenu statique, car toutes les ressources sont déjà générées et qu’il n’y aura aucune différence entre les fichiers si vous le faites manuellement (les fichiers de thème sont également en lecture seule, vous ne pouvez pas les modifier). Par conséquent, une telle opération n’a aucun sens.

## Solution

Si vous souhaitez toujours exécuter le déploiement de contenu statique, supprimez les liens symboliques dans le répertoire `pub/static` et exécutez à nouveau la commande `setup:static-content:deploy` :

```
find pub/static/ -maxdepth 1 -type l -delete
```
