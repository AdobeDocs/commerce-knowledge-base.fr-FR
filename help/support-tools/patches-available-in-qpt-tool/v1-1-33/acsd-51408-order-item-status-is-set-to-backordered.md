---
title: 'ACSD-51408 : l’état de l’élément de commande est incorrectement défini sur [!UICONTROL backordered]'
description: Appliquez le correctif ACSD-51408 pour résoudre le problème Adobe Commerce où l’état de l’élément de commande est incorrectement défini sur [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408 : l’état de l’élément de commande est incorrectement défini sur *[!UICONTROL backordered]*

Le correctif ACSD-51408 corrige le problème en raison duquel l’état de l’élément de commande est incorrectement défini sur [!UICONTROL backordered]. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.33 est installé. L’ID de correctif est ACSD-51408. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état de l’élément de commande est incorrectement défini sur *[!UICONTROL backordered]*.

<u>Conditions préalables</u> :

Les modules Adobe Commerce B2B et Inventory management (MSI) sont installés.

<u>Étapes à reproduire</u> :

1. Créez un site web, un magasin et une vue de magasin.
1. Créez une source.
1. Créez un nouveau stock lié au nouveau site web créé à l&#39;étape 1 et affectez la source créée à l&#39;étape 2.
1. Créez une société et affectez-la au nouveau site web créé à l’étape 1.
1. Créez un client et affectez-le à la société créée à l’étape 4.
1. Créez un produit, affectez-le au nouveau site web, puis définissez **[!UICONTROL default stock]** = *0* et **[!UICONTROL new stock]** sur une valeur supérieure à *0*.
1. Activez **[!UICONTROL backorders]**.
1. Activez le mode de paiement **[!UICONTROL Check/Money Order]** pour la nouvelle portée du site web.
1. Activez le **[!UICONTROL Flat Rate shipping method]** pour la nouvelle portée du site web.
1. Créez une nouvelle commande à partir de **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Sélectionnez le nouveau client créé à l’étape 5.
1. Sélectionnez le nouveau magasin créé à l’étape 1.
1. Sélectionnez le produit créé à l’étape 6.
1. Renseignez les informations de la commande, y compris les modes de paiement et de livraison.
1. Envoyez la commande.
1. Vérifiez le *Statut de l’élément*.

<u>Résultats attendus</u>

L’article peut être expédié à partir de l’inventaire. L’état de l’élément est *[!UICONTROL ordered]*.

<u>Résultats réels</u>

L’état de l’élément est *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[L’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est 0.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
