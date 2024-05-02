---
title: 'MDVA-35286 : erreur lors du passage en caisse de plusieurs adresses en une seule page'
description: Le correctif MDVA-35286 corrige le problème en raison duquel une erreur se produisait lorsqu’un client possédait un lot de produits dans le panier et passait de l’extraction à l’extraction à une seule page. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 est installé. L’ID de correctif est MDVA-35286. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286 : erreur lors du passage en caisse de plusieurs adresses en une seule page

Le correctif MDVA-35286 corrige le problème en raison duquel une erreur se produisait lorsqu’un client possédait un lot de produits dans le panier et passait de l’extraction à l’extraction à une seule page. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.18 est installée. L’ID de correctif est MDVA-35286. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur s’affiche si le panier contient un produit groupé et que l’utilisateur tente d’utiliser l’option Achat d’une page après avoir abandonné l’option Achat de plusieurs envois.

<u>Étapes à reproduire</u>:

1. Connectez-vous au compte client et ajoutez plusieurs produits regroupés au panier.
1. Cliquez sur le lien pour afficher et modifier le panier.
1. Cliquez sur le bouton **Extraction avec plusieurs adresses** lien.
1. Sélectionnez différentes adresses pour les produits ajoutés au panier.
1. Cliquez sur **Retour au panier**.
1. Dans le panier, cliquez sur **Passez à l’extraction**.

<u>Résultats attendus</u>:

Vous êtes redirigé vers la page Passage en caisse .

<u>Résultats réels</u>:

Le message d&#39;erreur s&#39;affiche : *Une erreur s’est produite lors du traitement de votre requête.*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
