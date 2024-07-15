---
title: 'ACSD 49843 : lien de téléchargement de produit indisponible après la facturation automatique avec [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Appliquez le correctif ACSD-49843 pour résoudre le problème Adobe Commerce en raison duquel le lien de téléchargement de produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843 : lien de téléchargement de produit indisponible après la facturation automatique avec [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

Le correctif ACSD-49843 corrige le problème en raison duquel le lien de téléchargement du produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale]. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.37 est installé. L’ID de correctif est ACSD-49843. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le lien de téléchargement du produit n’est pas disponible une fois que l’article commandé est automatiquement facturé par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale].

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur Adobe Commerce et accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Dans la liste déroulante [!UICONTROL Payment Action], sélectionnez **[!UICONTROL Intent Sale]** et définissez *[!UICONTROL Enable Card Payments]* sur *Oui*.

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**, et assurez-vous qu’il est défini sur *&quot;Invotered&quot;*.
1. Dans le storefront, connectez-vous en tant que client.

   * Ajoutez tout produit téléchargeable et un produit simple au panier.
   * Utilisez [!DNL Braintree Pay] pour passer la commande à l’aide de l’option de carte.

1. Accédez à **[!UICONTROL My Orders]** et vérifiez que la facture est automatiquement créée pour la commande et que les deux statuts de l&#39;article sont *&quot;Facturé&quot;*.
1. Accédez à **[!UICONTROL My Downloadable Products]** et observez que le lien de téléchargement n’est pas encore disponible.
1. Dans l’administrateur, accédez à cette commande et créez une expédition pour celle-ci.
1. Dans le storefront, accédez à **[!UICONTROL My Downloadable Products]** et observez que le lien de téléchargement est désormais disponible.

<u>Résultats attendus</u> :

Le lien de téléchargement est disponible lorsque l’état du produit téléchargeable est *&quot;Invocable&quot;*.

<u>Résultats réels</u> :

Le lien de téléchargement n’est pas disponible même lorsque l’état du produit téléchargeable indique *&quot;Invoqué&quot;*. Il n’est disponible qu’après la création d’une expédition pour le produit physique.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
