---
title: "Échec du déploiement : impossible d’appliquer le correctif MDVA-43395"
description: Cet article fournit une solution au problème, où la tentative d’application du correctif MDVA-43395 entraîne l’échec du déploiement.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Échec du déploiement : impossible d’appliquer le correctif MDVA-43395

Cet article fournit une solution au problème, où la tentative d’application du correctif MDVA-43395 entraîne l’échec du déploiement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Vous ne pouvez pas appliquer le correctif MDVA-43395.

## Cause

Les commerçants cloud n’ont pas besoin d’appliquer le correctif MDVA-43395 séparément s’ils ont [magento/magento-cloud-Correctifs 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) installé, qui inclut déjà le correctif.

## Solution

Pour résoudre ce problème, supprimez les correctifs MDVA-43395 et MDVA-43443 du `m2-hotfixes` et redéployez.

Si vous avez pu appliquer le correctif MDVA-43443 via l’événement `m2-hotfixes` , vous devez toujours le supprimer comme mentionné ci-dessus. Les correctifs déjà contenus dans les futures versions d’Adobe Commerce peuvent donc entraîner l’échec du déploiement si vous effectuez une mise à niveau ultérieure.

Pour vérifier si le correctif a été appliqué, exécutez le `vendor/bin/magento-patches -n status |grep 43443` .
S’il affiche plusieurs résultats de ce type, vous devez supprimer le correctif MDVA-43443 du `m2-hotfixes` folder:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Lecture connexe

* [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.
* [Correctifs cloud pour Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) dans notre documentation destinée aux développeurs.
