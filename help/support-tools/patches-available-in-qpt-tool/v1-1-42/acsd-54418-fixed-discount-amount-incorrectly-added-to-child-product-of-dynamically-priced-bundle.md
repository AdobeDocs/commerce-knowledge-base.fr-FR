---
title: "ACSD-54418 : montant de remise fixe ajouté de manière incorrecte au produit enfant d’un regroupement à prix dynamique"
description: Appliquez le correctif ACSD-54418 pour corriger le problème Adobe Commerce où le montant de remise fixe est incorrectement appliqué à chaque produit enfant du lot à prix dynamique.
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418 : Correction d’un montant de remise ajouté de manière incorrecte au produit enfant d’un regroupement à prix dynamique.

Le correctif ACSD-54418 corrige le problème en raison duquel le montant de remise fixe est incorrectement appliqué à chaque produit enfant du lot à prix dynamique. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.42 est installé. L’ID de correctif est ACSD-54418. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant de remise fixe est incorrectement appliqué à chaque produit enfant du lot à prix dynamique.

<u>Étapes à reproduire</u> :

1. Créez un **[!UICONTROL bundle product]** avec des options de tarification dynamique et un lot *2*.
1. Créez un **[!UICONTROL cart price rule]** avec un code de bon spécifique qui s’applique uniquement au produit **[!UICONTROL SKU]** regroupé et qui a une remise fixe.
1. Ajoutez le produit fourni au panier.
1. Appliquez le **[!UICONTROL coupon code]**.
1. Vérifiez la remise appliquée au panier.

<u>Résultats attendus</u> :

La remise n’est appliquée qu’une seule fois à l’ensemble du produit regroupé.

<u>Résultats réels</u> :

La remise est appliquée à chaque produit enfant groupé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
