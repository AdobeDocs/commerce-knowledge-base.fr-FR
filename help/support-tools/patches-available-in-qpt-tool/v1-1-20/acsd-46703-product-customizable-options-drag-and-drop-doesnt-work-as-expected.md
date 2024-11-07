---
title: "ACSD-46703 : le glisser-déposer de la personnalisation du produit ne fonctionne pas"
description: Cet article fournit une solution au problème où le glisser-déposer des options personnalisables du produit ne fonctionne pas comme prévu.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703 : Le glisser-déposer de la personnalisation du produit ne fonctionne pas

Le correctif ACSD-46703 corrige le problème en raison duquel les options personnalisables du produit (glisser-déposer) ne fonctionnent pas comme prévu. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-46703. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec les nouvelles versions de l’[ outil de correctifs de qualité]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas faire glisser les options personnalisables d’une page vers une autre.

<u>Étapes à reproduire</u> :

1. Créez un produit simple.
1. Ajoutez des options personnalisables au produit simple et veillez à ajouter plus de 20 options, ce qui se traduit par une pagination.
1. Essayez de déplacer une option personnalisable (par glisser-déposer) dans la même page.
1. Essayez maintenant de déplacer une option personnalisable de la page deux vers la page un.

<u>Résultats attendus</u> :

* Vous pouvez faire glisser les options personnalisables d’une page vers une autre.
* Vous pouvez trier les valeurs à l’aide de la fonctionnalité de glisser-déposer, même pour plusieurs pages.

<u>Résultats réels</u> :

Vous ne pouvez pas déplacer de valeur vers une autre page à l’aide de la fonctionnalité de glisser-déposer.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Outils de correctifs de qualité > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de l’outil Correctifs de qualité.
