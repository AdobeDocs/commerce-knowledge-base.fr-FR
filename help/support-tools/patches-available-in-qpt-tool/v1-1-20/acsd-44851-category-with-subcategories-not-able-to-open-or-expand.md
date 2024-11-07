---
title: "ACSD-44851 : catégorie avec des sous-catégories qui ne peuvent pas s’ouvrir ni se développer"
description: Cet article fournit une solution au problème où l’utilisateur ne peut pas ouvrir ou développer une catégorie avec des sous-catégories.
exl-id: 46ad9f9d-ed66-44df-b66d-ab9ff3923c36
feature: Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-44851 : catégorie dont les sous-catégories ne peuvent pas s’ouvrir ou se développer

Le correctif ACSD-44851 résout le problème où l’utilisateur ne peut pas ouvrir ou développer une catégorie avec des sous-catégories. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-44851. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur ne peut pas ouvrir ni développer une catégorie avec des sous-catégories.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur Adobe Commerce, créez une arborescence de catégories comportant deux catégories racine et quelques sous-catégories pour chacune d’elles.
1. Ouvrez l’affichage/l’émulateur mobile ou réduisez la largeur de la fenêtre jusqu’à ce que la mise en page atteigne le mobile.
1. Ouvrez le menu principal du catalogue.
1. Essayez de développer les catégories racine.
1. Essayez d’ouvrir la catégorie.

<u>Résultats attendus</u> :

Le menu est accessible.

<u>Résultats réels</u> :

Le second niveau du menu mobile ne s’ouvre pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Outils de correctifs de qualité > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil de correctifs de qualité.

* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de l’outil Correctifs de qualité.
