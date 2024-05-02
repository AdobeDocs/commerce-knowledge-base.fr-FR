---
title: "MDVA-23845 : impossible de prévisualiser le modèle de courrier électronique lorsque la minification JS est activée"
description: Le correctif du Magento MDVA-23845 corrige le problème lorsqu’il est impossible de prévisualiser le modèle de courrier électronique dans Admin lorsque la minification JS est activée.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845 : impossible de prévisualiser le modèle de courrier électronique lorsque la minification JS est activée.

Le correctif du Magento MDVA-23845 corrige le problème lorsqu’il est impossible de prévisualiser le modèle de courrier électronique dans Admin lorsque la minification JS est activée.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.20 est installée. L’ID de correctif est MDVA-23845. Veuillez noter que le problème a été corrigé dans la version 2.3.5 du Magento.

## Produits et versions concernés

**Le correctif est créé pour la version du Magento :** Magento Commerce Cloud 2.3.3

**Compatible avec les versions de Magento :** Magento Commerce et Commerce Cloud Magneto 2.3.2-2.3.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Activer **Minimisation JS** in **Admin > Magasins > Configuration > Paramètres JavaScript > Réduire les fichiers JavaScript** = *Oui* .
1. Passez le Magento en mode de production.
1. Accédez à **Admin > Marketing > Communications > Modèles de courrier électronique** .
1. Cliquez sur **Ajouter un modèle** .
1. Sélectionnez la variable **Nouvelle commande** modèle.
1. Cliquez sur le bouton **Charger le modèle** bouton .
1. Remplissage **Nom du modèle** avec **Nouvelle Ordre.**
1. Cliquez sur le bouton **Enregistrer le modèle** bouton .
1. Dans la grille Modèles d&#39;email, cliquez sur **Aperçu** dans le **Actions** colonne .

<u>Résultats attendus</u> :

L’aperçu du modèle d’email s’affiche dans la fenêtre contextuelle ouverte, comme prévu.

<u>Résultats réels</u> :

L&#39;aperçu du modèle d&#39;email n&#39;apparaît pas dans la fenêtre contextuelle ouverte. La fenêtre contextuelle est vide et des erreurs JS peuvent s’afficher.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre produit Magento :

* Magento Commerce : DevDocs [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud : DevDocs [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Correctif pour un problème de Magento avec l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
