---
title: "Échec du déploiement : impossible d’appliquer le correctif MDVA-43395"
description: Cet article fournit une solution au problème, où la tentative d’application du correctif MDVA-43395 entraîne l’échec du déploiement.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Les commerçants cloud n’ont pas besoin d’appliquer le correctif MDVA-43395 séparément s’ils ont installé [magento/magento-cloud-Correctifs 1.0.16](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016), qui inclut déjà le correctif.

## Solution

Pour résoudre ce problème, supprimez les correctifs MDVA-43395 et MDVA-43443 du répertoire `m2-hotfixes` et redéployez-les.

Si vous avez pu appliquer le correctif MDVA-43443 via le répertoire `m2-hotfixes`, vous devez toujours le supprimer comme mentionné ci-dessus. Les correctifs déjà contenus dans les futures versions d’Adobe Commerce peuvent donc entraîner l’échec du déploiement si vous effectuez une mise à niveau ultérieure.

Pour vérifier si le correctif a été appliqué, exécutez la commande `vendor/bin/magento-patches -n status |grep 43443`.
S’il affiche plusieurs résultats de ce type, vous devez supprimer le correctif MDVA-43443 du dossier `m2-hotfixes` :

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Lecture connexe

* [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.
* [Correctifs cloud pour Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) dans notre documentation destinée aux développeurs.
