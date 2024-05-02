---
title: "ACSD-51792 : la page ne comporte pas d’événement d’impression"
description: Appliquez le correctif ACSD-51792 pour résoudre le problème de performances d’Adobe Commerce en raison duquel une page ne comporte pas l’événement d’impression lorsque Google Tag Manager 4 est activé.
exl-id: 59194d4c-c387-4372-a0ff-1cdd74f8c6df
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51792 : la page ne comporte pas d’événement d’impression

Le correctif ACSD-51792 corrige le problème de performances lorsqu’une page ne comporte pas l’événement d’impression lorsque [!DNL Google Tag Manager] 4 est activé. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.33 est installée. L’ID de correctif est ACSD-51792. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La page ne comporte pas d’événement d’impression lorsque [!DNL Google Tag Manager] 4 est activé.

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Configurez la variable **[!DNL GoogleTag Manager]** intégration.
1. Accédez à [Assistant de balises Google](https://tagassistant.google.com/)et suivez les étapes nécessaires pour vous connecter à votre site web.
1. Ouvrez une page de catégorie qui comporte une liste de produits sur le storefront.
1. Recherchez l’événement d’impressions dans l’observateur de l’assistant de balises.

<u>Résultats attendus</u>:

L’événement d’impression doit commencer par tous les produits de la page.

<u>Résultats réels</u>:

La page ne comporte pas l’événement d’impression en tant qu’observateur de l’assistant de balises.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
