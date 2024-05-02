---
title: "ACSD-48773 : modèle d’email de points de récompense provenant d’un mauvais magasin"
description: Appliquez le correctif ACSD-48773 pour résoudre le problème Adobe Commerce en raison duquel le modèle d’email des points de récompense provient d’un mauvais magasin.
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773 : modèle d’email de points de récompense provenant d’un mauvais magasin

Le correctif ACSD-48773 corrige le problème en raison duquel le modèle d’email de points de récompense est extrait du mauvais magasin. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.26 est installée. L’ID de correctif est ACSD-48773. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation des prix du produit ne fonctionne pas si le produit du lot n’est affecté à aucun site web.

<u>Étapes à reproduire</u>:

1. Créez 2 sites web, 2 magasins et 2 vues de magasin.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** et activez **[!UICONTROL Reviews]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Basculez vers le **[!DNL default website scope]**, puis définissez la variable **[!UICONTROL Customer Support Sender Email]** address, (par exemple : *support_base@example.com*).
Basculez vers le **[!DNL second website scope]**, puis définissez la variable **[!UICONTROL Customer Support Sender Email]** adresse à une autre valeur (par exemple : *support_second@example.com*).
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**, et définissez **[!UICONTROL Share Customer Accounts]** = *Par site web*.
1. Sous **[!UICONTROL Reward Points]**, définissez les options suivantes :
   **[!UICONTROL Enable Reward Points Functionality]** = *Oui*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Oui*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** et défini **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** et défini **[!UICONTROL Email Sender]** = *Assistance clientèle*
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** et configurer les taux d’exchange du deuxième site web pour les deux **[!UICONTROL Points/Currency]** et **[!UICONTROL Currency/Points]**.
1. Créez un compte client sur le deuxième site web.
1. Connectez-vous en tant que client sur le deuxième site web.
1. Assurez-vous d’activer **[!UICONTROL Subscribe]** pour **[!UICONTROL Balance Updates]**.
1. Envoyez une révision de produit.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Modifiez l’état de la nouvelle révision en ***[!UICONTROL Approved]*** et **[!UICONTROL Save]**.
1. Attendez que l&#39;email arrive.

<u>Résultats attendus</u>:

L&#39;email de mise à jour des points de récompense doit avoir été envoyé par l&#39;expéditeur de l&#39;email configuré sur la deuxième portée du site web.

<u>Résultats réels</u>:

L’email de mise à jour des points de récompense a été envoyé par l’expéditeur de l’email configuré sur la portée par défaut du site web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
