---
title: 'MDVA-34102 : quantité vendable incohérente'
description: Le correctif MDVA-34102 résout le problème en raison duquel la quantité de stock par défaut est zéro pour les produits désactivés sur la grille de produits et les pages Modifier le produit dans l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 est installé. L’ID de correctif est MDVA-34102. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102 : quantité vendable incohérente

Le correctif MDVA-34102 résout le problème en raison duquel la quantité de stock par défaut est zéro pour les produits désactivés sur la grille de produits et les pages Modifier le produit dans l’administrateur. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.18 est installée. L’ID de correctif est MDVA-34102. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Configurez deux sites web avec des magasins et des vues de magasin.
1. Créez une source et un stock supplémentaires.
1. Ajoutez un produit simple :
   * Définir **Activer le produit** = *Non*.
   * Affectez deux sources à **État de l’élément source** = *En stock* avec une quantité supérieure à zéro (par exemple : **stock par défaut** = *123* et **actions britanniques** = *123*).
1. Enregistrez le produit.
1. Vérifiez les **Quantité vendable de produit** .

<u>Résultats attendus</u>:

Le stock par défaut et le stock britannique = *123.*

La quantité de stock par défaut s’affiche correctement pour les produits désactivés dans les pages Grille de produits et Modifier le produit dans l’administrateur.

<u>Résultats réels</u>:

Le stock par défaut = *0* et le stock britannique = *123.*

Le stock par défaut est nul pour les produits désactivés sur les pages Grille de produits et Modifier le produit dans l’administrateur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
