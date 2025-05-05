---
title: 'ACSD-51358 : les mises à jour de planification sont manquantes'
description: Appliquez le correctif ACSD-51358 pour résoudre le problème Adobe Commerce en raison duquel les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358 : les mises à jour de planification sont manquantes

Le correctif ACSD-51358 corrige le problème en raison duquel les modifications apportées à la mise à jour planifiée sans date de fin entraînaient la suppression d’autres mises à jour planifiées sur la même entité. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 est installé. L’ID de correctif est ACSD-51358. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.

<u>Étapes à reproduire</u> :

1. Créez un **[!UICONTROL scheduled update]** sans date de fin (*mettre à jour 1*).
1. Créez **[!UICONTROL scheduled update]** avec la même date de début que la première mise à jour, mais ajoutez le jour suivant et la date de fin (*mise à jour 2*).
1. Modifiez **[!UICONTROL scheduled update]** créé à l&#39;étape 1 (*mettre à jour 1*) et enregistrez les modifications.

<u>Résultats attendus</u>

La (*mise à jour 2*) doit rester dans la liste **[!UICONTROL schedule update]** lorsque (*mise à jour 1*) est modifiée.

<u>Résultats réels</u>

La (*mise à jour 2*) a été supprimée de la liste **[!UICONTROL schedule update]** lorsque (*mise à jour 1*) est modifiée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
