---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* entraîne une erreur lors de l’activation du bouton Précédent du navigateur."
description: Appliquez le correctif ACSD-48404 pour résoudre le problème Adobe Commerce où *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* provoque une erreur lorsque vous appuyez sur le bouton Précédent du navigateur.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404 : *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* génère une erreur lorsque vous appuyez sur le bouton Précédent du navigateur.

Le correctif ACSD-48404 corrige le problème où *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* provoque une erreur lorsque vous appuyez sur le bouton Précédent du navigateur. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.27 est installée. L’ID de correctif est ACSD-48404. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* provoque une erreur lorsque vous appuyez sur le bouton Précédent du navigateur.


<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**, puis définissez la variable *[!UICONTROL Remember Category Pagination]* to *Oui*.
1. Ouvrez une catégorie sur le storefront.
1. Sélectionnez une valeur qui n’est pas la valeur par défaut dans le *[!UICONTROL Show Per Page]* menu déroulant. Après avoir sélectionné une option, la page se recharge.
1. Une fois la page rechargée, cliquez sur un produit de la page de catalogue.
1. Sur la page des détails du produit ouverte, cliquez sur le **[!UICONTROL Back]** du navigateur.

<u>Résultats attendus</u>:

La page du catalogue s’ouvre à nouveau.

<u>Résultats réels</u>:

La page de catégorie renvoie une erreur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
