---
title: 'MDVA-36253 : Total incorrect dans le mini-panier après suppression d’un article'
description: Le correctif MDVA-36253 résout le problème en raison duquel le prix du produit n’est pas mis à jour si vous revenez à la page du mini-panier après avoir supprimé un produit lors de l’utilisation de l’étape de paiement multi-expédition. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-36253. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253 : Total incorrect dans le mini-panier après suppression d’un élément

Le correctif MDVA-36253 résout le problème en raison duquel le prix du produit n’est pas mis à jour si vous revenez à la page du mini-panier après avoir supprimé un produit lors de l’utilisation de l’étape de paiement multi-expédition. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.22 est installée. L’ID de correctif est MDVA-36253. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Total incorrect dans le mini-panier après suppression de l’élément.

<u>Étapes à reproduire</u>:

1. Connectez-vous en tant que client avec au moins une adresse.
1. Ajoutez quatre produits au panier (prix = 10 $ pour chacun).
1. Accédez au panier et cliquez sur **Extraction avec plusieurs adresses**.
1. Supprimez un élément.
1. Revenez à la page d’accueil.
1. Ouvrez le panier et vérifiez le prix total.

<u>Résultats attendus</u>:

Le total est de 30 $.

<u>Résultats réels</u>:

Le total est de 40 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
