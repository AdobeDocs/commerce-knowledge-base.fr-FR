---
title: '''ACSD-58163 : [!UICONTROL Cart Price Rule] n''applique pas de réduction à partir du panier [!UICONTROL Customer Segment] correspondant sans code de coupon'''
description: Appliquez le correctif ACSD-58163 pour résoudre le problème Adobe Commerce où [!UICONTROL Cart Price Rule] n’applique pas de réduction pour un invité du panier [!UICONTROL Customer Segment] correspondant sans code de bon.
feature: Products
role: Admin, Developer
source-git-commit: 7603a482953dc0ac0784ab6e6d3b22e4245e3e75
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-58163 : [!UICONTROL Cart Price Rule] n&#39;applique pas de réduction à partir du panier [!UICONTROL Customer Segment] correspondant sans code de coupon

Le correctif ACSD-58163 corrige le problème en raison duquel [!UICONTROL Cart Price Rule] n’applique pas de remise du panier [!UICONTROL Customer Segment] correspondant sans code de bon. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-58163. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule] n&#39;applique pas de réduction pour un invité du panier [!UICONTROL Customer Segment] correspondant sans code de coupon.

<u>Étapes à reproduire</u> :

1. Créer un segment client :
   * Pour les visiteurs.
   * Avec la condition pour avoir un produit dans le panier.

1. Créez un *[!UICONTROL Cart Price Rule]* :
   * Sans code de coupon.
   * Avec la condition pour qu’elle corresponde au segment client visiteur.

1. Créez un produit simple.
1. Ouvrez le storefront en tant qu&#39;invité.
1. Ajoutez un produit simple au panier.
1. Allez dans le panier.

<u>Résultats attendus</u> :

La remise *[!UICONTROL Cart Price Rule]* est appliquée.

<u>Résultats réels</u> :

La remise *[!UICONTROL Cart Price Rule]* n’est pas appliquée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
