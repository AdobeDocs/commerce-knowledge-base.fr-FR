---
title: 'ACSD-49706 : valeur par défaut enregistrée pour l’attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée'
description: Appliquez le correctif ACSD-49706 pour résoudre le problème Adobe Commerce en raison duquel une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706 : valeur par défaut enregistrée pour l’attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée

Le correctif ACSD-49706 corrige le problème d’enregistrement d’une valeur par défaut pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.29 est installée. L’ID de correctif est ACSD-49706. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Cliquez sur **[!UICONTROL Add New Attribute]**.
1. Renseignez les champs.

   * Par exemple, choisissez le type d’entrée *[!UICONTROL Visual Swatch]* et ajoutez plusieurs options (telles que *Rouge*, *Vert*). Veillez à choisir l’une de ces options par défaut.
   * Cliquez sur **[!UICONTROL Save Attribute]**.

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Modifiez la variable *[!UICONTROL Default]* ensemble d’attributs.
1. Déplacer *[!UICONTROL New Attribute]* de la colonne *[!UICONTROL Unassigned Attributes]* à la fonction *[!UICONTROL Product Details]* dans la colonne du milieu.

   * Cliquez sur **[!UICONTROL Save]**.

1. Créez un produit à l’aide du *[!UICONTROL Default]* ensemble d’attributs.

   * Laissez le champ *[!UICONTROL New Attribute]* vide et enregistrez-le.

1. Une fois enregistrée, une valeur apparaît dans *[!UICONTROL New Attribute]*.

<u>Résultats attendus</u>:

Aucune valeur n’est affectée à *[!UICONTROL New Attribute]* par défaut.

<u>Résultats réels</u>:

Une valeur par défaut est appliquée à l’attribut lors de l’enregistrement d’un produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
