---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** option ne fonctionne pas lors du tri des produits dans le  [!DNL Visual Merchandiser]'
description: Appliquez le correctif ACSD-56790 pour résoudre le problème Adobe Commerce en raison duquel l’option de retrait du stock vers le bas ne fonctionne pas lors du tri des produits dans le marchandisage visuel.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790 : l’option **[!UICONTROL move out of stock to bottom]** ne fonctionne pas lors du tri des produits dans le [!DNL Visual Merchandiser]

Le correctif ACSD-56790 corrige le problème où l’option de retrait du stock vers le bas ne fonctionne pas lors du tri des produits dans [!DNL Visual Merchandiser]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 est installé. L’ID de correctif est ACSD-56790. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’option **[!UICONTROL move out of stock to bottom]** ne fonctionne pas lors du tri des produits dans le [!DNL Visual Merchandiser]

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et créez les attributs suivants.
1. Créez un site web : **Non-main**.
1. Créez un **magasin non principal** sur ce nouveau site Web.
1. Créez deux magasins :

   * Commencez par le **magasin de site web principal**.
   * Second dans le **non-main Store**.

1. Créez deux sources :
   * Lettres.
   * Nombres.

1. Créez deux stocks :
   * First Main - canaux de vente : site web principal - sources affectées : lettres.
   * Second Non-main - canaux de vente : Non-main - sources affectées : Nombres.

1. Créez trois produits simples sur les deux sites web, tous dans la catégorie Par défaut, tous affectés aux deux sources :

   * ProductA - Qté *10* en lettres, Qté *0* en nombres.
   * Product1 - Qté *0* en lettres, Qté *10* en nombres.
   * ProductA1 - Qté *10* en lettres, Qté *10* en nombres.

1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** et sélectionnez **[!UICONTROL Default category]**.
1. Remplacez la portée par **First**.
1. Développez la section Produits de la catégorie .
1. Choisissez l’ordre de tri comme suit : **[!UICONTROL move out of stock to bottom]**

<u>Résultats attendus</u> :

La liste des produits avec les produits **en rupture de stock** est déplacée vers le bas.

<u>Résultats réels</u> :

Le chargement des produits échoue. Une page redirige vers le tableau de bord de l’administrateur avec le message d’erreur : `Invalid security or form key. Please refresh the page`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
