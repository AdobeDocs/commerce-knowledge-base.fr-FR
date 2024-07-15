---
title: "ACSD-55610 : La commande partiellement annulée a un montant de remise incorrect"
description: Appliquez le correctif ACSD-55610 pour résoudre le problème Adobe Commerce lorsqu’une commande partiellement annulée présente un montant de remise incorrect.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610 : La commande partiellement annulée présente un montant de remise incorrect.

Le correctif ACSD-55610 corrige le problème lorsqu’une commande partiellement annulée présente un montant de remise incorrect. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.43 est installé. L’ID de correctif est ACSD-55610. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une commande partiellement annulée présente un montant de remise incorrect.

<u>Étapes à reproduire</u> :

1. Créez une règle de prix de panier.

   * *[!UICONTROL Rule Name]* : *Solde d’hiver*
   * *[!UICONTROL Active]* = *Oui*
   * *[!UICONTROL Websites]* = *Site Web principal*
   * Sélectionnez tous les groupes de clients.
   * Sélectionnez un coupon spécifique.
   * *[!UICONTROL Coupon Code]* : *WINTER10*
   * *[!UICONTROL Conditions]* : *[!UICONTROL If ALL of these conditions are TRUE]* : *Sous-total(Exl. Taxe) est égale ou supérieure à 75*
   * Appliquez *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]* : *10*
   * *[!UICONTROL Discard subsequent rules]* : *Oui*

1. Créez trois produits dont les prix sont définis sur 100.
1. Ajoutez les trois produits au panier.
1. Appliquez le coupon.
1. Placez la commande.
1. Facturez un élément de la commande et envoyez-le.
1. Annuler les deux autres éléments.
1. Vérifiez la colonne `base_discount_canceled`.

<u>Résultats attendus</u> :

Le montant de la remise de `base_discount_cancelled` reflète correctement.

<u>Résultats réels</u> :

`base_discount_cancelled` n’est pas correct.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
