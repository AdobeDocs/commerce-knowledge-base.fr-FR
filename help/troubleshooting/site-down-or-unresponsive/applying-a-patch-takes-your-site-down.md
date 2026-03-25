---
title: L’application d’un correctif arrête votre site
description: Cet article aborde le problème d’un correctif que vous venez d’appliquer qui entraîne l’arrêt de votre site. Pour résoudre ce problème, vous pouvez supprimer le correctif.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# L’application d’un correctif arrête votre site

Cet article aborde le problème d’un correctif que vous venez d’appliquer qui entraîne l’arrêt de votre site. Pour résoudre ce problème, vous pouvez supprimer le correctif.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement), toutes les versions prises en charge
* Magento Open Source, toutes versions

## Problème

Après avoir appliqué un correctif, votre site tombe en panne.

## Cause

Ce problème peut se produire en raison d’une incompatibilité de version entre le correctif que vous venez d’appliquer à votre site web, vos personnalisations, d’autres correctifs que vous avez appliqués par le passé ou d’une autre erreur.

## Solution

Retirez le correctif. La méthode de suppression des correctifs est différente pour Adobe Commerce sur les infrastructures cloud et pour Adobe Commerce On-premise et Magento Open Source.

### Magento Open Source, toutes les versions 1.X

Pour les versions Magento Open Source 1.X,

* Exécutez la commande SSH suivante : `h SUPEE_patch --revert `

### Adobe Commerce On-premise, Magento Open Source, toutes les versions 2.x

Pour les versions Adobe Commerce on-premise et Magento Open Source 2.x,

1. Exécutez la commande SSH suivante :

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Si la commande ci-dessus ne fonctionne pas, essayez d’utiliser `-p2` au lieu de `-p1`)

1. Pour que les modifications soient prises en compte, actualisez le cache dans l’Admin sous **Système** > **Gestion du cache**.

### Adobe Commerce sur les infrastructures cloud, toutes versions confondues

Pour Adobe Commerce sur les infrastructures cloud, toutes les versions,

1. Supprimez le ou les fichiers `%patch_name%.composer.patch` du répertoire `m2-hotfixes`.
1. Validez et envoyez vos modifications de code :

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Lecture connexe

* [Comment appliquer un correctif de compositeur fourni par Adobe &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) dans notre base de connaissances d’assistance.
