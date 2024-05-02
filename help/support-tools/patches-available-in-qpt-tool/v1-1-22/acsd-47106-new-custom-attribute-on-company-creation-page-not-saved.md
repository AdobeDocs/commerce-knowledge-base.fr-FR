---
title: "ACSD-47106 : nouvel attribut personnalisé sur la page de création de l’entreprise non enregistré"
description: Appliquez le correctif ACSD-47106 pour résoudre le problème Adobe Commerce en raison duquel une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur la page de création d’une entreprise.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106 : nouvel attribut personnalisé sur la page de création de l’entreprise non enregistré

Le correctif ACSD-47106 corrige le problème lorsqu’une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur la page de création d’une entreprise. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.22 est installée. L’ID de correctif est ACSD-47106. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur la page de création d’une entreprise.

<u>Conditions préalables</u>:

* Les modules B2B sont installés.

<u>Étapes à reproduire</u>:

1. Accédez à Administration Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Créer un attribut : _Test 01_.
1. Accédez à l’administrateur Commerce > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > et créez une nouvelle société avec tous les détails requis.
1. Essayez d’ajouter une valeur à l’attribut personnalisé. _Test 01_.
1. Tentative de mise à jour de la valeur de l’attribut personnalisé _Test 01_.

<u>Résultats attendus</u>:

Les modifications sont enregistrées.

<u>Résultats réels</u>:

Les modifications ne sont pas enregistrées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
