---
title: '''ACSD-46770 : l''email de confirmation de commande est envoyé même lorsque [!UICONTROL Email Order Confirmation] n’est pas coché"'
description: Appliquez le correctif ACSD-46770 pour résoudre le problème Adobe Commerce en raison duquel les emails de confirmation de commande sont envoyés même lorsque [!UICONTROL Email Order Confirmation] n’est pas sélectionnée.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770 : l&#39;email de confirmation de commande est envoyé même lorsque **[!UICONTROL Email Order Confirmation]** n’est pas coché

Le correctif ACSD-46770 corrige le problème en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité, même lorsque **[!UICONTROL Email Order Confirmation]** n’est pas sélectionnée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.24 est installée. L’ID de correctif est ACSD-46770. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un email de confirmation de commande est envoyé même lorsque **[!UICONTROL Email Order Confirmation]** n’est pas sélectionnée.

<u>Étapes à reproduire</u>:

1. Créez un compte client.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Order]** et cliquez sur  **[!UICONTROL Create New Order]**.
1. Sélectionnez le client, ajoutez les produits à la commande, renseignez l’adresse et sélectionnez les modes de livraison et de paiement.
1. Avant d’envoyer la commande, désélectionnez l’option **[!UICONTROL Email Order confirmation]** .
1. Cliquez sur **[!UICONTROL Submit Order]** pour créer l’ordre.

<u>Résultats attendus</u>:

Un email de confirmation de commande ne doit pas être envoyé si la variable **[!UICONTROL Email Order Confirmation]** n’est pas sélectionnée.

<u>Résultats réels</u>:

Un email de confirmation de commande est envoyé, indépendamment de la désélection **[!UICONTROL Email Order Confirmation]** .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
