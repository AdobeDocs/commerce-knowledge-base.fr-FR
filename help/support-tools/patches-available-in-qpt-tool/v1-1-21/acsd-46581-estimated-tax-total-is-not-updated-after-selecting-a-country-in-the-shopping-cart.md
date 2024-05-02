---
title: "ACSD-46581 : le total estimé des impôts n’est pas mis à jour après la sélection d’un pays dans le panier"
description: Appliquez le correctif ACSD-46581 pour résoudre le problème Adobe Commerce où le taux d’imposition n’est pas mis à jour après avoir changé de pays dans le panier.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581 : Le total estimé de la taxe n’est pas mis à jour après la sélection d’un pays dans le panier.

Ce correctif ACSD-46581 résout le problème en raison duquel le taux d’imposition n’est pas mis à jour après le changement de pays dans le panier. Il n’est mis à jour qu’après avoir sélectionné le mode de livraison. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.21 est installée. L’ID de correctif est ACSD-46581. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de la taxe n’est pas mis à jour après le changement de pays dans le panier.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur Adobe Commerce, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Créer un nouveau taux de taxe pour **[!UICONTROL Country]** = _États-Unis_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8,25_.
1. Créer un nouveau taux de taxe pour **[!UICONTROL Country]** = _Inde_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Créez une règle fiscale avec les taux d&#39;imposition pour les Etats-Unis et l&#39;Inde.
1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** et activer plusieurs méthodes d’expédition (_Taux d&#39;aplatissement_ et _Livraison gratuite_ par exemple).
1. Créez un produit simple avec la méthode **[!UICONTROL Taxable Goods]** classe fiscale.
1. Ajoutez le produit au panier au premier plan du magasin.
1. Ouvrez le panier et vérifiez le montant de la taxe.
1. Les paramètres de taxe par défaut pour les États-Unis sont appliqués et la taxe est calculée sur la base d’un taux de 8,25 %.
1. Passez le pays en Inde.

<u>Résultats attendus</u>:

Le montant de l&#39;impôt a changé à 10% lors du changement de pays en Inde.

<u>Résultats réels</u>:

Le montant de la taxe reste le même dans la section totale du panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
