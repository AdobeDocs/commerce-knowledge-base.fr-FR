---
title: L’application d’un correctif réduit votre site.
description: Cet article traite du problème où un correctif que vous venez d’appliquer entraîne la fermeture de votre site. Pour le résoudre, vous pouvez supprimer le correctif.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# L’application d’un correctif réduit votre site.

Cet article traite du problème où un correctif que vous venez d’appliquer entraîne la fermeture de votre site. Pour le résoudre, vous pouvez supprimer le correctif.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement), toutes les versions prises en charge
* Magento Open Source, toutes versions

## Problème

Une fois que vous avez appliqué un correctif, votre site tombe en panne.

## Cause

Ce problème peut apparaître en raison d’une incompatibilité de version entre le correctif que vous venez d’appliquer à votre site web, vos personnalisations, d’autres correctifs que vous avez appliqués dans le passé ou d’une autre erreur.

## Solution

Supprimez le correctif. La méthode de suppression des correctifs diffère pour Adobe Commerce sur l’infrastructure cloud par rapport à Adobe Commerce sur site et Magento Open Source.

### Magento Open Source, toutes les versions 1.X

Pour les versions de Magento Open Source 1.X,

* Exécutez la commande SSH suivante : `h SUPEE_patch --revert `

### Adobe Commerce sur site, Magento Open Source, toutes les versions 2.x

Pour les versions Adobe Commerce On-Premise et Magento Open Source 2.x,

1. Exécutez la commande SSH suivante :

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1`)

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.

### Adobe Commerce sur l’infrastructure cloud, toutes les versions

Pour Adobe Commerce sur l’infrastructure cloud, toutes les versions,

1. Supprimez le `%patch_name%.composer.patch` fichier(s) du `m2-hotfixes` répertoire .
1. Validez et envoyez vos modifications de code :

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Lecture connexe

* [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.
