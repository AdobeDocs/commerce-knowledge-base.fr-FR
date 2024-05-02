---
title: 'ACSD-51149: Planifié [!UICONTROL ImportExport] avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs'
description: Appliquez le correctif ACSD-51149 pour résoudre le problème de performances d’Adobe Commerce lorsque la variable [!UICONTROL ImportExport] avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149 : Planifié [!UICONTROL ImportExport] avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs

Le correctif ACSD-51149 corrige le problème où le [!UICONTROL ImportExport] avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-51149. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Planifié [!UICONTROL ImportExport] avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs.

<u>Étapes à reproduire</u>:

1. Activer *[!UICONTROL Catalog Permissions]*.
1. Définir tous les indexeurs sur *[!UICONTROL Update by Schedule]*.
1. Créez un produit simple.
1. Exporter ce produit via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Téléchargez le fichier CSV exporté et collez-le dans `<AC root folder>/var/import`.
1. Créez une importation de produit planifiée avec le fichier CSV téléchargé.
1. Exécutez la réindexation complète.
1. Vérifiez l’état des indexeurs. Tous les indexeurs doivent se trouver dans *[!UICONTROL Ready]* statut.
1. Exécutez l’importation planifiée créée à partir de la grille.
1. Vérifiez l’état des indexeurs.

<u>Résultats attendus</u>:

Tous les indexeurs se trouvent dans la variable *[!UICONTROL Ready]* statut.

<u>Résultats réels</u>:

Certains des indexeurs se trouvent dans *[!UICONTROL Reindex Required]* statut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
