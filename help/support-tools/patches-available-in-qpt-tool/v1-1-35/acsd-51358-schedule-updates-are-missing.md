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

Le correctif ACSD-51358 corrige le problème en raison duquel les modifications apportées à la mise à jour planifiée sans date de fin entraînaient la suppression d’autres mises à jour planifiées sur la même entité. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.35 est installée. L’ID de correctif est ACSD-51358. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.

<u>Étapes à reproduire</u>:

1. Créez un **[!UICONTROL scheduled update]** sans la date de fin (*update 1*).
1. Créer **[!UICONTROL scheduled update]** avec la même date de début que la première mise à jour, mais ajoutez le jour suivant et la date de fin (*update 2*).
1. Modifier **[!UICONTROL scheduled update]** créé à l’étape 1 (*update 1*) et les modifications d’enregistrement.

<u>Résultats attendus</u>

(*update 2*) doit rester dans la variable **[!UICONTROL schedule update]** répertorier quand (*update 1*) est modifié.

<u>Résultats réels</u>

(*update 2*) a été supprimé de la variable **[!UICONTROL schedule update]** répertorier quand (*update 1*) est modifié.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
