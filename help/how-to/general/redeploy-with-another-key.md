---
title: 'Adobe Commerce on cloud : modification des clés d’authentification et redéploiement'
description: Cet article explique comment redéployer Adobe Commerce sur une infrastructure cloud avec différentes clés d’authentification. Par exemple, il se peut que vous ayez utilisé les clés d’un autre compte ou que vous ayez utilisé des clés Magento Open Source au lieu de clés Adobe Commerce.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%
---
# Adobe Commerce on cloud : modification des clés d’authentification et redéploiement

Cet article explique comment redéployer Adobe Commerce sur une infrastructure cloud avec différentes clés d’authentification. Par exemple, il se peut que vous ayez utilisé les clés d’un autre compte ou que vous ayez utilisé des clés Magento Open Source au lieu de clés Adobe Commerce.

Si vous avez utilisé des clés incorrectes, le déploiement échoue. Pour effectuer une récupération, vous devez cloner le projet, ajouter les clés appropriées à `auth.json` et pousser la modification vers la branche principale.

Dans cet article, nous supposons que votre projet comporte uniquement une branche `master` (`master` est la branche par défaut lorsque vous créez un projet pour la première fois).

Pour redéployer avec les clés d’authentification correctes :

1. Connectez-vous à la machine sur laquelle se trouve votre Adobe Commerce sur les clés SSH de l’infrastructure cloud.
1. Connectez-vous au projet :

   ```
   magento-cloud login
   ```

1. Créez une branche pour mettre à jour le code `auth` :

   ```
   magento-cloud environment:branch auth master
   ```

1. Accédez au répertoire racine du projet.
1. Ouvrez `auth.json` dans un éditeur de texte.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Ajoutez les clés d’authentification appropriées.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Validez et fusionnez vos modifications.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Attendez que le déploiement soit terminé.

Les messages indiquent si le déploiement a réussi. Vous pouvez confirmer la réussite du déploiement en accédant à l’un des **itinéraires d’environnement** affichés à l’écran.
