---
title: 'ACSD-48634: [!DNL JS] Erreurs lorsque [!DNL Google Analytics Content Experiments] enabled'
description: Application du correctif ACSD-48634 pour corriger [!DNL JS] Erreurs sur un [!DNL staging] mettre à jour la page lorsque [!DNL Google Analytics Content Experiments] est activée.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634 : [!DNL JS] Erreurs lorsque [!DNL Google Analytics Content Experiments] enabled

Correctifs ACSD-48634 [!DNL JS] Erreurs sur un [!DNL staging] mettre à jour la page lorsque [!DNL Google Analytics Content Experiments] est activée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.27 est installée. L’ID de correctif est ACSD-48634. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL JS] des erreurs se produisent sur un [!DNL staging] mettre à jour la page lorsque [!DNL Google Analytics Content Experiments] est activée.

<u>Étapes à reproduire</u>:

1. Dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, créez un site web, un magasin et un **[!UICONTROL Store View]**. Assurez-vous que la variable **[!UICONTROL Store View]** is *[!UICONTROL Enabled]*.
1. Configurer **[!DNL Configure Google Analytics]** en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Pour **[!DNL Main]** et sites web supplémentaires [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* pour les autres champs, mais ne les modifiez pas.
   * Pour **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Désactiver **[!DNL Configure Google Analytics]** on **[!DNL Default Config]** [!DNL scope] en modifiant **[!UICONTROL Enable]** de *[!UICONTROL Yes]* to *[!UICONTROL No]*. Veillez à ne rien changer d&#39;autre !
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Créez et modifiez des **[!UICONTROL category]** et ajoutez une mise à jour planifiée pour celle-ci :
   * N’importe quel nom, date de début dans le futur, date de fin dans le futur et toute modification dans **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Enregistrez la mise à jour et vérifiez le [!DNL browser developer console] pour les erreurs.

<u>Résultats attendus</u>:

Non [!DNL JS] et les modifications apportées à la variable [!DNL staging] Les mises à jour sont enregistrées correctement.

<u>Résultats réels</u>:

[!DNL JS] les erreurs sont visibles dans la console, le formulaire est mal formé et la variable [!DNL spinner] ne sera jamais désactivé après l’enregistrement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
