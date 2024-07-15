---
title: '''ACSD-54965 : [!UICONTROL Visual Merchandising] la grille n''affiche pas le bon stock'''
description: Appliquez le correctif ACSD-54965 pour résoudre le problème Adobe Commerce en raison duquel la grille [!UICONTROL Visual Merchandising] n’affiche pas le stock correct lorsqu’un produit est affecté à un stock personnalisé.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965 : [!UICONTROL Visual Merchandising] la grille n&#39;affiche pas le stock correct

Le correctif ACSD-54965 corrige le problème en raison duquel la grille [!UICONTROL Visual Merchandising] n’affiche pas le stock correct lorsqu’un produit est affecté à un stock personnalisé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 est installé. L’ID de correctif est ACSD-54965. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La grille [!UICONTROL Visual Merchandising] n’affiche pas le stock correct lorsqu’un produit est affecté à un stock personnalisé.

<u>Étapes à reproduire</u> :

1. Créez une source.
1. Créez un nouveau stock.
1. Créez deux produits :
   * Un produit avec le stock personnalisé uniquement.
   * Un produit avec le stock par défaut uniquement.
1. Ajoutez ces produits à une catégorie.
1. Accédez à la grille [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Résultats réels</u> :

Dans les portées *[!UICONTROL All Store Views]*, le produit avec du stock personnalisé n’affiche aucune quantité. Ce n’est que lorsque la portée *[!UICONTROL Default Store View]* est sélectionnée que le stock personnalisé indique la quantité du produit.

<u>Résultats attendus</u> :

La grille affiche toutes les informations sur les stocks si la portée est *[!UICONTROL All Store Views]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
