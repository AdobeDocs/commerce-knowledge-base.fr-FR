---
title: '''ACSD-47920 : un utilisateur invité peut passer des commandes via l''API REST même lorsque [!UICONTROL Allow Guest Checkout] is off'''
description: Appliquez le correctif ACSD-47920 pour résoudre le problème Adobe Commerce en raison duquel les commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même lorsque la variable [!UICONTROL Allow Guest Checkout] est désactivé.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920 : un utilisateur invité peut passer des commandes via l’API REST même lorsque **[!UICONTROL Allow Guest Checkout]** est désactivé

Le correctif ACSD-47920 corrige le problème en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité, même lorsque la variable **[!UICONTROL Allow Guest Checkout]** est désactivé. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.24 est installée. L’ID de correctif est ACSD-47920. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même lorsque la variable **[!UICONTROL Allow Guest Checkout]** est désactivé.

<u>Étapes à reproduire</u>:

1. Accédez à Administration Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > et définissez **[!UICONTROL Allow Guest Checkout]** to _Non_.
1. Utilisez l’API REST pour ajouter un produit à un panier et passer une commande.

<u>Résultats attendus</u>:

L’API de paiement des invités renvoie une erreur *[!UICONTROL Sorry, guest checkout is not available]* if **[!UICONTROL Allow Guest Checkout]** est défini sur _Non_.

<u>Résultats réels</u>:

L’API de passage en caisse des invités permet de passer une commande même si **[!UICONTROL Allow Guest Checkout]** est défini sur _Non_.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
