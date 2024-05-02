---
title: "ACSD-46703 : le glisser-déposer de la personnalisation du produit ne fonctionne pas"
description: Cet article fournit une solution au problème où le glisser-déposer des options personnalisables du produit ne fonctionne pas comme prévu.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703 : Le glisser-déposer de la personnalisation du produit ne fonctionne pas

Le correctif ACSD-46703 corrige le problème en raison duquel les options personnalisables du produit (glisser-déposer) ne fonctionnent pas comme prévu. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.20 est installée. L’ID de correctif est ACSD-46703. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [Outil Correctifs de qualité] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas faire glisser les options personnalisables d’une page vers une autre.

<u>Étapes à reproduire</u>:

1. Créez un produit simple.
1. Ajoutez des options personnalisables au produit simple et veillez à ajouter plus de 20 options, ce qui se traduit par une pagination.
1. Essayez de déplacer une option personnalisable (par glisser-déposer) dans la même page.
1. Essayez maintenant de déplacer une option personnalisable de la page deux vers la page un.

<u>Résultats attendus</u>:

* Vous pouvez faire glisser les options personnalisables d’une page vers une autre.
* Vous pouvez trier les valeurs à l’aide de la fonctionnalité de glisser-déposer, même pour plusieurs pages.

<u>Résultats réels</u>:

Vous ne pouvez pas déplacer de valeur vers une autre page à l’aide de la fonctionnalité de glisser-déposer.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Outils de correctifs de qualité > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil Correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de l’outil Correctifs de qualité.
