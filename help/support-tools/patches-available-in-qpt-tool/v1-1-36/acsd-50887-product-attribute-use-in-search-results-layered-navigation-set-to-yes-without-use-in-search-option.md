---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* défini sur Oui sans le *[!UICONTROL Use in Search]* option'
description: Appliquez le correctif ACSD-50887 pour résoudre le problème Adobe Commerce où la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être défini sur *Oui* sans le *[!UICONTROL Use in Search]* est également définie sur *Oui*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887 : *[!UICONTROL Use in Search Results Layered Navigation]* défini sur *Oui* sans le *[!UICONTROL Use in Search]* option

Le correctif ACSD-50887 corrige le problème où la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être défini sur *Oui* sans le *[!UICONTROL Use in Search]* est également définie sur *Oui*. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.36 est installée. L’ID de correctif est ACSD-50887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être défini sur *Oui* sans le *[!UICONTROL Use in Search]* est également définie sur *Oui*.

Ces paramètres ont été conçus pour être utilisés ensemble. Lorsque le correctif est appliqué, lorsque la variable *[!UICONTROL Use in Search]* est définie sur *Non*, la variable *[!UICONTROL Use in Search Results Layered Navigation]* est masquée pour fonctionner comme si elle était également définie sur *Non*.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** et créez un attribut avec le type multiselect et définissez les éléments suivants :

   * *[!UICONTROL Use in Search]= Non*
   * *[!UICONTROL Use in Layered Navigation]= (N’importe quelle option)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Oui*
   * *Nom = Test_attribute*
   * *Options*:
      * *Attrapeur*
      * *Sélecteur*

1. Ajoutez le nouvel attribut au jeu d’attributs par défaut.
1. Créez deux produits :

   1. Premier produit :
      * Nom = Sticker
      * Définir le prix, la qualité, le poids sur 1
      * Test_attribute = option de sélection *Attrapeur*

   1. Deuxième produit :
      * Nom = Sélecteur
      * Définir le prix, la qualité, le poids sur 1
      * Test_attribute = sélectionner les deux options

1. Exécuter `catalogsearch_fulltext` reindex :

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Recherche par mot *sticker* sur la vitrine.

<u>Résultats attendus</u>:

Uniquement le produit *Attrapeur* est renvoyé, car [!DNL Elasticsearch] n’indexe pas Test_attribute lorsque *[!UICONTROL Use in Search]* a été défini sur *Non*.

<u>Résultats réels</u>:

Les deux produits sont renvoyés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
