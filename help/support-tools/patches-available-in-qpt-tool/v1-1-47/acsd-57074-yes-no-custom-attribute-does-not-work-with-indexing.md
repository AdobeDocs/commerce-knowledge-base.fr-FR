---
title: '"ACSD-57074: *Oui/Non* attribut personnalisé avec le préfixe "price_*" dans l’attribut "attribute_code" ne fonctionne pas avec l’indexation"'
description: Appliquez le correctif ACSD-57074 pour résoudre le problème Adobe Commerce en raison duquel l’attribut personnalisé *Oui/Non* avec le préfixe `price_*` dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074 : *Oui/Non* attribut personnalisé avec `price_*` dans `attribute_code` ne fonctionne pas avec l’indexation.

Le correctif ACSD-57074 corrige le problème où la variable *Oui/Non* attribut personnalisé avec `price_*` dans le `attribute_code` ne fonctionne pas avec l’indexation. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.47 est installée. L’ID de correctif est ACSD-57074. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La variable *Oui/Non* attribut personnalisé avec `price_*` dans le `attribute_code` ne fonctionne pas avec l’indexation.

<u>Étapes à reproduire</u>:

1. Créez un attribut de produit personnalisé avec les options suivantes :
   * *[!UICONTROL Catalog Input Type]*: *Oui/Non*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Oui*
1. Attribuez l’attribut au jeu d’attributs par défaut.
1. Créez un produit avec l’attribut que nous avons créé.
1. Attribuez le produit que nous venons de créer à une catégorie.
1. Exécutez la réindexation complète.

<u>Résultats attendus</u>:

Le produit s’affiche dans la catégorie qui lui est assignée.

<u>Résultats réels</u>:

Le produit n’apparaît pas sur la page de catégorie de premier plan.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
