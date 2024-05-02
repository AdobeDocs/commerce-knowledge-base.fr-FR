---
title: "ACSD-49042 : le produit avec un ordre infini ne peut pas être commandé à partir du storefront"
description: Appliquez le correctif ACSD-49042 pour résoudre le problème d’Adobe Commerce en raison duquel un produit avec un ordre d’arrière-plan infini ne peut pas être commandé à partir du storefront.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042 : le produit avec un ordre infini ne peut pas être commandé à partir du storefront.

Le correctif ACSD-49042 corrige le problème lorsqu’un produit avec un ordre infini ne peut pas être commandé à partir du storefront. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.27 est installée. L’ID de correctif est ACSD-49042. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur se produit lorsqu’un produit avec un ordre d’arrière-plan infini ne peut pas être commandé à partir du storefront.

<u>Étapes à reproduire</u>:

1. Définissez les paramètres de configuration suivants :
   * **[!UICONTROL Display Out of Stock Products]** défini sur *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** défini sur *[!UICONTROL Allow Qty Below 0]*.
1. Ajouter un nouveau **[!DNL custom stock]** et **[!DNL custom source]**.
1. Attribuez un produit à la variable **[!DNL custom source]** et assurez-vous qu’un numéro d’inventaire est défini pour celui-ci (par exemple : *10*).
1. Sur la page de modification du produit, ouvrez **[!UICONTROL Advanced Inventory]**. Définissez la variable **[!UICONTROL minimum quantity]** dans le panier, (par exemple : *160*). La quantité doit être supérieure au stock.
1. Accédez au storefront et achetez un produit pour créer une réservation.
1. Modifiez la variable **[!UICONTROL product quantity]** to *0*. Le point essentiel est d’enregistrer le produit à partir du **[!DNL Admin panel]** lorsqu&#39;il y a une réservation.
1. Ouvrez le **[!UICONTROL product page]** sur le storefront et essayez d’ajouter le produit au panier.

<u>Résultats attendus</u>:

Il est possible d’ajouter le produit au panier car les commandes en arrière-plan pour une quantité inférieure à *0* sont autorisées.

<u>Résultats réels</u>:

Le produit s’affiche en rupture de stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
