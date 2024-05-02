---
title: 'ACSD-53925 : impossible d’enregistrer le bloc CMS avec [!UICONTROL Product Carousel]'
description: Appliquez le correctif ACSD-53925 pour résoudre le problème Adobe Commerce en raison duquel l’administrateur ne parvient pas à enregistrer un bloc CMS avec le carrousel de produit lorsque le mode dimensions pour "catalog_product_price" est défini sur le site web.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925 : impossible d’enregistrer le bloc CMS avec *[!UICONTROL Product Carousel]*

Le correctif ACSD-53925 corrige le problème lorsque l’administrateur ne parvient pas à enregistrer un bloc CMS avec *[!UICONTROL Product Carousel]* lorsque le mode dimensions pour `catalog_product_price` est définie sur le site web. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.43 est installée. L’ID de correctif est ACSD-53925. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur ne peut pas enregistrer de bloc CMS avec *[!UICONTROL Product Carousel]* lorsque le mode dimensions pour `catalog_product_price` est définie sur le site web.

<u>Étapes à reproduire</u>:

1. Créez deux produits simples :
   * simple1 - 10 $
   * simple2 - 20 $
1. Création d’un produit groupé&#x200B;*bundle1-dyn*&quot; avec deux options basées sur des SKU de produit simples.
1. Définissez le mode des dimensions pour l’indexeur de prix de produit :

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Blocks]** et créez un bloc CMS.
1. Modifiez le contenu à l’aide de [!DNL Page Builder]:
   * Ajouter un *[!UICONTROL Row]* element
   * Ajouter un *[!UICONTROL Products]* element
   * Sélectionner *[!UICONTROL Product Carousel]*
   * Saisie du SKU du produit - *bundle1-dyn*
1. Enregistrez le bloc CMS.

<u>Résultats attendus</u>:

L’utilisateur peut ajouter un carrousel de produit sans erreur.

<u>Résultats réels</u>:

* Un message s’affiche dans l’interface utilisateur : *Une erreur s’est produite lors de la génération de ce contenu.*
* `var/log/exception.log` contient l’erreur suivante :

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
