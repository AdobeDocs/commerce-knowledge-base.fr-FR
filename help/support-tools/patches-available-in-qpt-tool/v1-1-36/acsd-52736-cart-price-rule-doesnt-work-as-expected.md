---
title: "ACSD-52736 : [!UICONTROL Cart Price Rule] ne fonctionne pas comme prévu"
description: Appliquez le correctif ACSD-52736 pour résoudre le problème Adobe Commerce lorsqu’un [!UICONTROL Cart Price Rule] contenant les exigences relatives à la quantité configurable de produits ne fonctionne pas comme prévu.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736 : [!UICONTROL Cart Price Rule] ne fonctionne pas comme prévu

Le correctif ACSD-52736 corrige le problème lorsqu’un [!UICONTROL Cart Price Rule] contenant les exigences relatives à la quantité configurable de produits ne fonctionne pas comme prévu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 est installé. L’ID de correctif est ACSD-52736. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un [!UICONTROL Cart Price Rule] qui comprend les exigences relatives à la quantité configurable de produits ne fonctionne pas comme prévu.

<u>Étapes à reproduire</u> :

1. Créez une règle de panier :
   * [!UICONTROL Apply] = Pourcentage de remise sur le prix du produit
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Appliquez la règle uniquement aux articles du panier correspondant aux conditions suivantes : Quantité dans le panier = 1
2. Ajoutez un produit [!UICONTROL Qty] = 2 au panier.
3. Vérifiez les prix du panier.

<u>Résultats attendus</u> :

La règle n’est pas appliquée car la quantité de produits dans le panier est *2*.

<u>Résultats réels</u> :

La remise est appliquée.

<u> Étapes supplémentaires requises après l’installation du correctif </u> :

Après l’application du correctif, les conditions de la règle de panier utilisant l’attribut *Quantity* doivent être supprimées et ajoutées à nouveau.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
