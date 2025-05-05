---
title: "ACSD-48661 : problème de validation du séparateur virgule de limite de crédit de l’entreprise"
description: Appliquez le correctif ACSD-48661 pour corriger le problème Adobe Commerce où, lorsque la limite de crédit de l’entreprise est supérieure à 999, le séparateur de virgules empêche l’enregistrement de l’entreprise en raison d’une erreur de validation.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661 : problème de validation du séparateur virgule de limite de crédit de l’entreprise

Le correctif ACSD-48661 corrige le problème en raison duquel lorsque la limite de crédit de l’entreprise est supérieure à 999, le séparateur de virgules empêche l’enregistrement de l’entreprise en raison d’une erreur de validation. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 est installé. L’ID de correctif est ACSD-48661. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque la limite de crédit de l’entreprise est supérieure à 999, le séparateur des virgules empêche l’entreprise d’effectuer des économies en raison d’une erreur de validation.

<u>Étapes à reproduire</u> :

1. Activez la fonction d’entreprise à l’adresse **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Créez une société et ajoutez une limite de crédit supérieure à 999 sous l’onglet **[!UICONTROL Company Credit]**.
1. Enregistrez la société.
1. Modifiez la société et essayez de l’enregistrer à nouveau.

<u>Résultats attendus</u> :

Vous pouvez enregistrer la société sans corriger la limite de crédit. La virgule n’est pas prise en charge pour les champs de saisie pour les montants et les prix.

<u>Résultats réels</u> :

Vous ne pouvez pas enregistrer la société en raison d’une erreur de validation dans le champ *[!UICONTROL Credit Limit]*. Adobe Commerce ajoute automatiquement des séparateurs virgules pour les limites de crédit, même si le champ [!UICONTROL Credit Limit] n’accepte pas les virgules.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
