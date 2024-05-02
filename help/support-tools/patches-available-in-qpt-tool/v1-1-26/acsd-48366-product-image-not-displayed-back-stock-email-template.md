---
title: '''ACSD-48366 : image du produit non affichée sur [!UICONTROL Back to Stock] modèle d''email'''
description: Appliquez le correctif ACSD-48366 pour résoudre le problème Adobe Commerce en raison duquel l’image de miniature du produit ne s’affiche pas dans l’e-mail d’alerte de stock du produit.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366 : image du produit non affichée sur [!UICONTROL Back to Stock] modèle de courrier électronique

Le correctif ACSD-48366 corrige le problème en raison duquel l’image de miniature du produit ne s’affiche pas dans l’e-mail d’alerte du produit. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.26 est installée. L’ID de correctif est ACSD-48366. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’image du produit ne s’affiche pas sur la page [!UICONTROL Back to Stock] modèle de courrier électronique.

<u>Étapes à reproduire</u>:

1. Activer *[!UICONTROL Product Alert]* pour *[!UICONTROL Back in Stock]* en accédant à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Activer *[!UICONTROL Display Out of Stock Products]* en accédant à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Créez un produit simple avec qty = 0.
1. Créez un client à partir du storefront et abonnez-vous au produit ci-dessus pour obtenir des alertes de produit lorsqu’il est en stock.
1. Faites le produit en stock.
1. Exécutez le cron d’alerte du produit.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Lancez l’alerte de produit pour le client.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Vérifiez l&#39;email. Le message d’alerte Stock doit maintenant être disponible dans le receveur de courrier.

<u>Résultats attendus</u>:

L’image du produit s’affiche dans l’email d’alerte de stock.

<u>Résultats réels</u>:

L’image du produit n’est pas disponible dans l’email d’alerte de stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
