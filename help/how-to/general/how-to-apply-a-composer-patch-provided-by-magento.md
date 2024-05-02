---
title: Comment appliquer un correctif de compositeur fourni par Adobe
description: Cet article explique comment appliquer un correctif de compositeur pour Adobe Commerce sur site, Adobe Commerce sur l’infrastructure cloud et Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
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
1. Copiez le `%patch_name%.composer.patch` fichiers au `m2-hotfixes` répertoire .
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

Pour plus d’informations sur l’application de correctifs aux projets Cloud, voir [Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

### Comment appliquer un correctif de compositeur pour Adobe Commerce sur site et Magento Open Source {#commerce}

1. Téléchargez le correctif dans votre répertoire racine Adobe Commerce sur site ou Magento Open Source.
1. Exécutez la commande SSH suivante :

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1` )

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.
