---
title: "ACSD-59378 : Store-level [!DNL URL] réécrit incorrectement mis à jour lors de l’importation"
description: Appliquez le correctif ACSD-59378 pour résoudre le problème Adobe Commerce où les réécritures de niveau magasin  [!DNL URL] sont incorrectement mises à jour lors de l’importation.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 3f400c3e325c3f377a5e12170b08615ebeadbcd1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-59378 : le niveau du magasin [!DNL URL] réécrit incorrectement lors de l’importation.

Le correctif ACSD-59378 corrige le problème en raison duquel les réécritures au niveau du magasin [!DNL URL] sont incorrectement mises à jour lors de l’importation. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-59378. Veuillez noter que ce problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5x (toutes les versions de 2.4.5)

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les réécritures au niveau du magasin [!DNL URL] sont incorrectement mises à jour lors de l’importation.

<u>Étapes à reproduire</u> :

1. Créez un produit avec `url_key = key_default` sur la portée **Toutes les vues de magasin**.
1. Définissez `url_key = key_store` dans la portée **Vue de magasin par défaut**.
1. Exportez le produit.
1. Importez un fichier [!DNL CSV] pour ce produit avec les données suivantes :
   * La colonne `store_view_code` est définie sur *empty* afin qu’elle s’applique à la portée **Toutes les vues de magasin**.
   * `url_key` est défini sur la clé par défaut *`key_default`*.

<u>Résultats attendus</u> :

Les réécritures [!DNL URL] ne sont régénérées que pour les vues de magasin où il n’y a pas de remplacement `url_key` (où s’applique la valeur par défaut `url_key`).

<u>Résultats réels</u> :

Les réécritures `key_store` [!DNL URL] sont supprimées, mais la réécriture [!DNL URL] sur le niveau **Default Store View** pour le produit est toujours définie sur *`key_store`*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
