---
title: "ACSD-52160 : Résultat de validation du produit par rapport à la règle du prix du panier"
description: Appliquez le correctif ACSD-52160 pour résoudre le problème Adobe Commerce en raison duquel le résultat de la validation du produit par rapport à la règle de prix du panier n’est pas correctement évalué en fonction de la condition de règle *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160 : le résultat de la validation du produit par rapport à la règle de prix du panier n’est pas correctement évalué.

Le correctif ACSD-52160 corrige le problème en raison duquel le résultat de la validation du produit par rapport à la règle de prix du panier n’est pas correctement évalué en fonction de la condition de règle *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 est installé. L’ID de correctif est ACSD-52160. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le résultat de la validation du produit par rapport à la règle de prix du panier n’est pas correctement évalué en fonction de la condition de règle *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Étapes à reproduire</u> :

1. Créez deux produits affectés à deux catégories différentes.
1. Créez un **[!UICONTROL Cart Price Rule]** avec des conditions telles que :

   * **SKU 1** dans le paramètre *[!UICONTROL FOUND]*
   * **SKU 2** dans le paramètre *[!UICONTROL NOT FOUND]*

1. Ajoutez les deux produits au panier.
1. Appliquez le code du coupon.

<u>Résultats attendus</u>

Le code de coupon n’est pas appliqué, car le panier contient des produits de la catégorie restreinte.

<u>Résultats réels</u>

Le code de coupon est appliqué.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
