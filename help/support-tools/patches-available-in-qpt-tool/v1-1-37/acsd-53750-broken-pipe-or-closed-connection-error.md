---
title: '"ACSD-53750 : erreur "Tranche de tuyau ou connexion fermée" lors de la réindexation de catalogue_product_price multi-thread"'
description: Appliquez le correctif ACSD-53750 pour résoudre le problème Adobe Commerce en raison duquel une erreur de *pipeline rompu ou connexion fermée* survient lors de la réindexation de catalogue_product_price multi-thread.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750 : *Canalisation rompue ou connexion fermée* erreur lors d’une opération multi-thread `catalog_product_price` reindex

Le correctif ACSD-53750 corrige le problème en raison duquel une erreur *Canalisation rompue ou connexion fermée* survient lors d’une erreur multi-thread. `catalog_product_price` réindexer. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.37 est installée. L’ID de correctif est ACSD-53750. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*Canalisation rompue ou connexion fermée* survient lors d’une erreur multi-thread. `catalog_product_price` réindexer.

<u>Étapes à reproduire</u>:

1. Configurez RabbitMq.
1. Générer des exemples de données à l’aide de la `small.xml` fichier .
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** et défini **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Définissez le mode de dimension pour les index qui prennent en charge cette fonction. Par exemple, `catalog_product_price_website_and_customer_group` ou `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Exécution de la réinitialisation des indexeurs pour `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Exécutez l’indexeur pour l’indexeur de réinitialisation à l’aide de plusieurs threads.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Résultats attendus</u>:

Aucune erreur ne se produit.

<u>Résultats réels</u>:

L’erreur suivante est provoquée par une connexion AMQP : *Canalisation rompue ou connexion fermée*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
