---
title: '''ACSD-48417 : erreur SQL après la création d''un changement de planning'''
description: Appliquez le correctif ACSD-48417 pour résoudre le problème Adobe Commerce en raison duquel une erreur SQL s’affiche après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417 : erreur SQL après la création d&#39;un changement de planning

Le correctif ACSD-48417 corrige le problème d’apparition d’une erreur SQL après la création d’un changement de planification pour un produit et l’enregistrement d’un autre produit. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 est installé. L’ID de correctif est ACSD-48417. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur SQL s’affiche après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit.

<u>Étapes à reproduire</u> :

1. Installez Magento 2.4-develop EE + Sample Data.
1. Accédez au panneau d’administration > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Modifiez n’importe quel produit (par exemple, Joust Duffle Bag [SKU : 24-MB01]).
1. Planifiez une nouvelle mise à jour :
   * Sélectionner **[!UICONTROL Save as a New Update]**
   * Nom de la mise à jour : &quot;Update 1&quot;
   * Date de début : heure actuelle +1 min
   * Date de fin : heure actuelle + 1 heure
   * Modifiez le nom du produit en : &quot;Joust Duffle Bag 2&quot;
   * Enregistrez le produit.
1. Accédez à l’interface de ligne de commande et exécutez cron et attendez que le planning soit appliqué.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Encore une fois, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et modifiez tout produit configurable (par exemple, Chaz Kangeroo Hoodie [SKU : MH01]).

   * Désactivez toutes les variantes. Accédez à la colonne Actions > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Enregistrez la configuration.

<u>Résultats attendus</u> :

Aucune erreur ne s’est produite lors de l’enregistrement du produit.

<u>Résultats réels</u> :

L’erreur suivante se produit :

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
