---
title: Comment appliquer un correctif de compositeur fourni par Adobe
description: Cet article explique comment appliquer un correctif de compositeur pour Adobe Commerce sur site, Adobe Commerce sur l’infrastructure cloud et Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Comment appliquer un correctif de compositeur fourni par Adobe

Cet article explique comment appliquer un correctif de compositeur pour Adobe Commerce sur site, Adobe Commerce sur l’infrastructure cloud et Magento Open Source.

>[!WARNING]
>
>Nous vous recommandons vivement d’appliquer et de tester le correctif dans l’environnement d’évaluation/d’intégration avant de l’appliquer à la production. Nous vous recommandons également d’effectuer une sauvegarde récente avant toute manipulation.

## Comment appliquer un correctif de compositeur pour Adobe Commerce sur l’infrastructure cloud {#cloud}

1. Si vous ne disposez pas d’un répertoire nommé `m2-hotfixes` dans la racine du projet, créez-en un.
1. Copiez le ou les fichiers `%patch_name%.composer.patch` dans le répertoire `m2-hotfixes`.
1. Ajoutez, validez et poussez vos modifications de code :

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Pour plus d’informations sur l’application de correctifs aux projets Cloud, voir [Application de correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

### Comment appliquer un correctif de compositeur pour Adobe Commerce sur site et Magento Open Source {#commerce}

1. Téléchargez le correctif dans votre répertoire racine Adobe Commerce sur site ou Magento Open Source.
1. Exécutez la commande SSH suivante :

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1` )

1. Pour que les modifications soient prises en compte, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.
