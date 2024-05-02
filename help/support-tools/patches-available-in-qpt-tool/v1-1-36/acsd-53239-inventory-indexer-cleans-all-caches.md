---
title: "ACSD-53239 : l’indexeur de stock nettoie tous les caches"
description: Appliquez le correctif ACSD-53239 pour résoudre le problème Adobe Commerce en raison duquel l’indexeur d’inventaire nettoie tous les caches dans la variable [!UICONTROL Update on Schedule] mode .
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: b8e68cf7-d326-4c9e-8749-d83113de2070
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239 : l’indexeur de stock nettoie tous les caches dans la variable [!UICONTROL Update on Schedule] mode

Le correctif ACSD-53239 corrige le problème en raison duquel l’indexeur d’inventaire nettoie tous les caches dans la variable [!UICONTROL Update on Schedule] mode . Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.36 est installée. L’ID de correctif est ACSD-53239. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’indexeur d’inventaire nettoie tous les caches dans la variable [!UICONTROL Update on Schedule] mode .

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** et sélectionnez à propos *1200* produits.
2. Mettre à jour *[!UICONTROL Qty]* à une nouvelle valeur, puis cliquez sur **[!UICONTROL Save]**.
3. Exécuter `bin/magento cron:run` immédiatement après l’enregistrement.
4. Exécutez la requête GraphQL suivante :

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Résultats attendus</u>

La requête est traitée dans le temps habituel.

<u>Résultats réels</u>

Le traitement de la requête est exceptionnellement lent.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
