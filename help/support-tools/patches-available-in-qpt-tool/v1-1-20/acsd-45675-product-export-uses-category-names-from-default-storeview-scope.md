---
title: "ACSD-45675 : l’exportation de produits utilise des noms de catégorie de l’étendue de vue de magasin par défaut"
description: Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation de produits utilise des noms de catégorie de la portée d’affichage de magasin par défaut. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-45675. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675 : l’exportation de produits utilise des noms de catégorie de l’étendue de vue de magasin par défaut.

Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation de produits utilise des noms de catégorie de la portée d’affichage de magasin par défaut. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.20 est installée. L’ID de correctif est ACSD-45675. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation de produits utilise des noms de catégorie provenant de la portée de la vue de magasin par défaut.

<u>Étapes à reproduire</u>:

1. Création d’une vue de magasin personnalisée **[!UICONTROL Thai]** à l&#39;intérieur du magasin principal.
1. Make **[!UICONTROL Thai]** la vue de magasin par défaut du site web principal.
1. Créez la structure de catégorie suivante sous **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Sélectionner la catégorie **[!UICONTROL Tea]** et modifiez la variable **[!UICONTROL Scope]** to **[!UICONTROL Thai]**.
1. Définissez la variable **[!UICONTROL Category Name]** as **[!UICONTROL ชาดำ]**.
1. Création d’un produit simple **[!UICONTROL SP001]** et affecter la catégorie **[!UICONTROL Black]**.
1. Vérifiez que le cron ne s’exécute pas.
1. Exportez un produit. Filtrage par SKU et sélection **[!UICONTROL SP001]**.
1. Vérifiez les **[!UICONTROL categories]** dans le fichier CSV exporté.

<u>Résultats attendus</u>:

Comme aucun magasin n’a été sélectionné lors de l’exportation, vous devez obtenir un chemin de catégorie comme celui-ci : *[!UICONTROL Default Category/Tea/Black]*.

<u>Résultats réels</u>:

Le chemin d’accès aux catégories comporte plusieurs langues : *[!UICONTROL Default Category/ชาดำ/Black]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tools] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil Correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans [!DNL QPT], voir [Correctifs disponibles dans [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de l’outil Correctifs de qualité.
