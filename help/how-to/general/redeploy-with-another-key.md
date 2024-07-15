---
title: "Adobe Commerce on cloud : modifiez les clés d’authentification et redéployez"
description: Cet article fournit des instructions sur la manière de redéployer Adobe Commerce sur l’infrastructure cloud avec différentes clés d’authentification. Par exemple, vous avez peut-être utilisé les clés d’un autre compte ou des clés de Magento Open Source au lieu des clés Adobe Commerce.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce on cloud : modifiez les clés d’authentification et redéployez

Cet article fournit des instructions sur la manière de redéployer Adobe Commerce sur l’infrastructure cloud avec différentes clés d’authentification. Par exemple, vous avez peut-être utilisé les clés d’un autre compte ou des clés de Magento Open Source au lieu des clés Adobe Commerce.

Si vous avez utilisé des clés incorrectes, le déploiement échoue. Pour récupérer, vous devez cloner le projet, ajouter les clés correctes à `auth.json` et transmettre la modification à la branche principale.

Dans cet article, nous supposons que votre projet possède une branche `master` uniquement (`master` est la branche par défaut lors de la création initiale d’un projet).

Pour redéployer avec les clés d’authentification correctes :

1. Connectez-vous à l’ordinateur sur lequel votre Adobe Commerce se connecte à l’aide des clés SSH de l’infrastructure cloud.
1. Connectez-vous au projet :

   ```
   magento-cloud login
   ```

1. Créez une branche pour mettre à jour le code avec le nom `auth` :

   ```
   magento-cloud environment:branch auth master
   ```

1. Modifiez le répertoire racine du projet.
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

1. Ajoutez les clés d’authentification correctes.
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

Les messages indiquent si le déploiement a réussi. Vous pouvez confirmer un déploiement réussi en accédant à l’une des **routes d’environnement** affichées sur votre écran.
