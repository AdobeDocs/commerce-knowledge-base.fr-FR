---
title: "ACSD-47520 : les clients perdent des points de récompense lors de la création d’une note de crédit"
description: Appliquez le correctif ACSD-47520 pour résoudre le problème Adobe Commerce en raison duquel les clients perdent des points de récompense lorsqu’une note de crédit est créée.
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520 : les clients perdent des points de récompense lors de la création d’une note de crédit

Le correctif ACSD-47520 corrige le problème en raison duquel les clients perdent des points de récompense lors de la création d’une note de crédit. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 est installé. L’ID de correctif est ACSD-47520. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients perdent des points de récompense lorsqu’un avoir est créé.

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Modifiez le paramètre :
   * **[!UICONTROL Enable Reward Points Functionality]** = _Oui_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Oui_
   * **[!UICONTROL Customers May See Reward Points History]** = _Oui_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Non_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Oui_
1. Accédez à Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** et cliquez sur **[!UICONTROL Add New Rate]**.
1. Ajoutez un nouveau taux (1:1) et videz le cache.
1. Créez un client et ajoutez 10 points de récompense à ce compte.
1. Accédez à Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Sélectionnez le client créé à l’étape précédente.
1. Sélectionnez un produit dont le prix est supérieur aux points de récompense.
1. Passer une commande par n&#39;importe quel mode de paiement et les points de récompense.
1. Créez une facture pour la commande.
1. Créez une note de crédit, mais ne remboursez pas les points de récompense.

<u>Résultats attendus</u> :

* L&#39;administrateur peut rembourser les points de récompense.

* L’état de la commande est fermé.

<u>Résultats réels</u> :

* Il n&#39;y a aucun moyen de rembourser les points de récompense.

* L’état de la commande est **[!UICONTROL Completed]**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
