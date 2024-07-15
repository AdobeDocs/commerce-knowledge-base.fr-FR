---
title: '''MDVA-35092 : Erreur Vimeo : "Vidéo introuvable"'
description: '''Le correctif MDVA-35092 corrige le problème où vous voyez l’erreur : *"Vidéo introuvable"*. Ce message d’erreur s’affiche lorsque vous saisissez une vidéo Vimeo à l’aide de l’interface native Ajouter une vidéo dans l’administrateur de produit d’Adobe Commerce. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3."'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092 : Erreur Vimeo : &quot;Vidéo introuvable&quot;

Le correctif MDVA-35092 corrige le problème où vous voyez l’erreur : *&quot;Vidéo introuvable&quot;*. Ce message d’erreur s’affiche lorsque vous saisissez une vidéo Vimeo à l’aide de l’interface native Ajouter une vidéo dans l’administrateur de produit d’Adobe Commerce. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.5 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’API simple Vimeo cesse de fonctionner comme prévu.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur.
1. Pour modifier un produit existant, accédez à **CATALOG** > **Produits** > **Modifier**, ou pour créer un nouveau produit, accédez à **CATALOG** > **Produits** > **Modifier** > **Ajouter un produit**.
1. Cliquez sur l’onglet **Images et vidéos** de la page Produit.
1. Cliquez sur **Ajouter une vidéo** et ajoutez l’URL d’une vidéo Vimeo. Cliquez sur **Enregistrer**.

<u>Résultats attendus</u> :

La nouvelle vidéo est trouvée et enregistrée.

<u>Résultats réels</u> :

Erreur : *&quot;Vidéo introuvable&quot;* s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
