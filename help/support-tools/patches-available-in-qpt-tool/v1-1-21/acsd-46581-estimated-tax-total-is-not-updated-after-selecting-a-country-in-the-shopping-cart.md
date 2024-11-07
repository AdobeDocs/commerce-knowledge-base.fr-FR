---
title: "ACSD-46581 : le total estimé des impôts n’est pas mis à jour après la sélection d’un pays dans le panier"
description: Appliquez le correctif ACSD-46581 pour résoudre le problème Adobe Commerce où le taux d’imposition n’est pas mis à jour après avoir changé de pays dans le panier.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581 : Le total estimé de la taxe n’est pas mis à jour après la sélection d’un pays dans le panier.

Ce correctif ACSD-46581 résout le problème en raison duquel le taux d’imposition n’est pas mis à jour après le changement de pays dans le panier. Il n’est mis à jour qu’après avoir sélectionné le mode de livraison. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 est installé. L’ID de correctif est ACSD-46581. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de la taxe n’est pas mis à jour après le changement de pays dans le panier.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur Adobe Commerce, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Créez un nouveau taux d&#39;imposition pour **[!UICONTROL Country]** = _États-Unis_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Créez un nouveau taux d&#39;imposition pour **[!UICONTROL Country]** = _Inde_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Créez une règle fiscale avec les taux d&#39;imposition pour les Etats-Unis et l&#39;Inde.
1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** et activez plusieurs méthodes d’expédition (_Flat Rate_ et _Free Shipping_ par exemple).
1. Créez un produit simple avec la classe de taxe **[!UICONTROL Taxable Goods]**.
1. Ajoutez le produit au panier au premier plan du magasin.
1. Ouvrez le panier et vérifiez le montant de la taxe.
1. Les paramètres de taxe par défaut pour les États-Unis sont appliqués et la taxe est calculée sur la base d’un taux de 8,25 %.
1. Passez le pays en Inde.

<u>Résultats attendus</u> :

Le montant de l&#39;impôt a changé à 10% lors du changement de pays en Inde.

<u>Résultats réels</u> :

Le montant de la taxe reste le même dans la section totale du panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
