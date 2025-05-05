---
title: "ACSD-45675 : l’exportation de produits utilise des noms de catégorie de l’étendue de vue de magasin par défaut"
description: Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation de produits utilise des noms de catégorie de la portée d’affichage de magasin par défaut. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-45675. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675 : l’exportation de produits utilise des noms de catégorie de l’étendue de vue de magasin par défaut.

Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation de produits utilise des noms de catégorie de la portée d’affichage de magasin par défaut. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-45675. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation de produits utilise des noms de catégorie provenant de la portée de la vue de magasin par défaut.

<u>Étapes à reproduire</u> :

1. Créez une vue de magasin personnalisée **[!UICONTROL Thai]** dans le magasin principal.
1. Faites de **[!UICONTROL Thai]** la vue de magasin par défaut du site web principal.
1. Créez la structure de catégorie suivante sous **[!UICONTROL Default Category]** :

   *[!UICONTROL Default category/Tea/Black]*

1. Sélectionnez la catégorie **[!UICONTROL Tea]** et remplacez **[!UICONTROL Scope]** par **[!UICONTROL Thai]**.
1. Définissez le **[!UICONTROL Category Name]** sur **[!UICONTROL ชาดำ]**.
1. Créez un produit simple **[!UICONTROL SP001]** et affectez la catégorie **[!UICONTROL Black]**.
1. Vérifiez que le cron ne s’exécute pas.
1. Exportez un produit. Filtrez par SKU et sélectionnez **[!UICONTROL SP001]**.
1. Vérifiez la colonne **[!UICONTROL categories]** dans le fichier CSV exporté.

<u>Résultats attendus</u> :

Comme aucun magasin n’a été sélectionné lors de l’exportation, vous devez obtenir un chemin de catégorie du type : *[!UICONTROL Default Category/Tea/Black]*.

<u>Résultats réels</u> :

Le chemin de catégorie comporte plusieurs langues : *[!UICONTROL Default Category/ชาดำ/Black]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tools] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=fr) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans [!DNL QPT], reportez-vous à la section [Correctifs disponibles dans [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) du guide de l’outil Correctifs de qualité.
