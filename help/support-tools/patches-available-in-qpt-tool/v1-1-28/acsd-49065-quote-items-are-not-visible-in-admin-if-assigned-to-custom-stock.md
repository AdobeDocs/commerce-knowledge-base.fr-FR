---
title: "ACSD-49065 : les éléments entre guillemets ne sont pas visibles dans l’administration"
description: Appliquez le correctif ACSD-49065 pour résoudre le problème Adobe Commerce en raison duquel les éléments de guillemet ne sont pas visibles dans l’administrateur s’ils sont uniquement affectés au stock personnalisé.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065 : Les éléments entre guillemets ne sont pas visibles dans l’administration

Le correctif ACSD-49065 corrige le problème en raison duquel les éléments de guillemet ne sont pas visibles dans l’administrateur s’ils sont uniquement affectés au stock personnalisé. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.28 est installée. L’ID de correctif est ACSD-49065. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les éléments de guillemet ne sont pas visibles dans l’administrateur s’ils sont uniquement affectés au stock personnalisé.

Conditions préalables :

**[!UICONTROL B2B]** et **[!UICONTROL Inventory]** Les modules doivent être installés.

<u>Étapes à reproduire</u>:

1. Activer **[!UICONTROL Company]** et **[!UICONTROL B2B Quote]** under **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Création d’un secondaire **[!UICONTROL Inventory Source]** et l’affecter à un secondaire **[!UICONTROL Inventory Stock]**.
1. Créez un produit en attribuant uniquement le secondaire (non par défaut). **[!UICONTROL Inventory Source]**.
1. Accédez au storefront et créez un compte de société. Connectez-vous en tant que **[!UICONTROL Company Admin]**, puis ajoutez le produit créé au panier.
1. Accédez au panier et *[!UICONTROL Request a Quote]*.
1. Accédez à l’administrateur et consultez le devis demandé à l’adresse **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Résultats attendus</u>:

Les éléments sont visibles dans le nouveau guillemet créé avec de nouveaux produits sans réenregistrer les produits.

<u>Résultats réels</u>:

La variable *[!UICONTROL Items Quoted]* est vide. Si vous enregistrez à nouveau le produit nouvellement créé, les éléments s’affichent.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
