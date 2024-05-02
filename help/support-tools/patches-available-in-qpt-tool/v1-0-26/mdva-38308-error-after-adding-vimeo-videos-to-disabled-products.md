---
title: "MDVA-38308 : Erreur après l’ajout de vidéos Vimeo aux produits désactivés"
description: '''Le correctif de qualité MDVA-38308 pour Adobe Commerce résout le problème où les utilisateurs reçoivent le message d’erreur : *Remarque : Index non défini : extension à la ligne 806 de /lib/internal/Magento/Framework/File/Uploader.php,* lors de l’ajout de vidéos Vimeo à des produits désactivés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 est installé. L’ID de correctif est MDVA-38308. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4."'
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308 : Erreur après l’ajout de vidéos Vimeo aux produits désactivés.

Le correctif de qualité MDVA-38308 pour Adobe Commerce résout le problème où les utilisateurs reçoivent le message d’erreur : *Remarque : Index non défini : extension dans /lib/internal/Magento/Framework/File/Uploader.php sur la ligne 806,* lors de l’ajout de vidéos Vimeo aux produits désactivés. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.26 est installée. L’ID de correctif est MDVA-38308. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.4.1-p1, 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’ajout de vidéos Vimeo à des produits désactivés, vous recevez le message d’erreur suivant :  *Remarque : Index non défini : extension dans /lib/internal/Magento/Framework/File/Uploader.php sur la ligne 806*

<u>Étapes à reproduire</u>:

1. Créez un produit simple.
1. Désactivez le produit créé.
1. Essayez d’ajouter une vidéo Vimeo au produit désactivé.

<u>Résultats attendus</u>:

La vidéo est ajoutée sans erreur.

<u>Résultats réels</u>:

Vous obtenez l’erreur suivante :
*Remarque : Index non défini : extension dans /lib/internal/Magento/Framework/File/Uploader.php sur la ligne 806*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de qualité dans notre base de connaissances de support, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de notre base de connaissances en matière de soutien.
