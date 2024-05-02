---
title: 'MDVA-30782 : le bloc dynamique est affiché quelle que soit la règle du panier'
description: Le correctif MDVA-30782 corrige le problème d’affichage d’un bloc dynamique, quelle que soit la règle du panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782 : le bloc dynamique est affiché quelle que soit la règle du panier.

Le correctif MDVA-30782 corrige le problème d’affichage d’un bloc dynamique, quelle que soit la règle du panier. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.7 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le bloc dynamique s&#39;affiche sur la page même lorsque la condition de la règle de prix du catalogue associée n&#39;est pas remplie.

<u>Étapes à reproduire</u>:

1. Créez deux produits.
1. Créez une règle de prix de catalogue applicable uniquement à l’un de ces produits.
1. Créez un bloc dynamique et affectez-lui la règle de prix de catalogue nouvellement créée.
1. Créez un widget avec les paramètres suivants :
   * Type = Rotateur de bloc dynamique
   * Blocs dynamiques à afficher = blocs dynamiques spécifiés
   * Spécifier les blocs dynamiques = étape de bloc de formulaire \#3Layout Mises à jour (peut-être n’importe quelle)
   * Afficher sur = Tous les types de produits
   * Conteneur = Informations auxiliaires du produit
1. Réindexez et videz le cache.
1. Vérifiez les deux pages de produit pour l’étape de formulaire de bloc dynamique \#3

<u>Résultats attendus</u>:

Le bloc dynamique apparaît uniquement sur la première page de produit.

<u>Résultats réels</u>:

Le bloc dynamique apparaît sur les deux pages de produit. Avec des blocs dynamiques à afficher = règle de prix du catalogue associée à l’étape \#3, le résultat est le même.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
