---
title: 'ACSD-50367 : L’exportation de l’adresse du client ne fonctionne pas avec un attribut à sélection multiple'
description: Appliquez le correctif ACSD-50367 pour résoudre le problème Adobe Commerce en raison duquel l’exportation de l’adresse du client ne fonctionne pas lors de la création d’un attribut **’adresse du client** à sélection multiple.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367 : L’exportation des adresses client ne fonctionne pas

Le correctif ACSD-50367 corrige le problème lorsque l’exportation de l’adresse du client ne fonctionne pas lorsqu’une sélection multiple **`Customer Address`** est créé sans valeurs. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.30 est installée. L’ID de correctif est ACSD-50367. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation des adresses client ne fonctionne pas lorsqu’une sélection multiple **`Customer Address`** est créé sans valeurs.

<u>Conditions préalables</u>:

Créez un client avec une adresse.

<u>Étapes à reproduire</u>:

1. Création d’une sélection multiple **`Customer Address`** dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**, puis sélectionnez **`Customer Address`** type d’entité.
1. Exportez les adresses du client. Vous verrez que rien n&#39;est exporté.
1. Supprimer la sélection multiple **`Customer Address`** et exporter à nouveau les adresses du client. Cette fois, le fichier CSV des adresses est généré.

<u>Résultats attendus</u>:

Les adresses du client peuvent être exportées sous forme de fichier CSV lors d’une sélection multiple. **`Customer Address`** est créé.

<u>Résultats réels</u>:

Les adresses du client ne peuvent pas être exportées en tant que fichier CSV lors d’une sélection multiple **`Customer Address`** est créé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
