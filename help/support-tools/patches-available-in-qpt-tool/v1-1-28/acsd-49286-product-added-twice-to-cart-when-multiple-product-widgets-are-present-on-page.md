---
title: "ACSD-49286 : produit ajouté deux fois au panier en présence de plusieurs widgets de produit"
description: Appliquez le correctif ACSD-49286 pour résoudre le problème Adobe Commerce en raison duquel le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286 : produit ajouté deux fois au panier en présence de plusieurs widgets de produit

Le correctif ACSD-49286 corrige le problème en raison duquel le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.28 est installée. L’ID de correctif est ACSD-49286. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Dans la section Contenu, cliquez sur **[!UICONTROL Edit]** using [!DNL Page Builder].
1. Ajoutez deux éléments de ligne à **[!UICONTROL Content]**.
1. Ajoutez des produits aux deux éléments de ligne.
1. Dans la première ligne, définissez l’aspect du produit sur [!UICONTROL Product Grid] et sélectionnez une catégorie à afficher.
1. Dans la deuxième ligne, définissez l’aspect du produit sur [!UICONTROL Product Carousel] et sélectionnez toute autre catégorie à afficher.
1. Aller à la vitrine **[!UICONTROL Home Page]**, puis ajoutez un produit à partir de la grille de produits.
1. Ajouter un autre produit depuis [!UICONTROL Product Carousel].

<u>Résultats attendus</u>:

La quantité de produit ne doit pas doubler après l’ajout d’un produit au panier à partir de [!UICONTROL Product Grid].

<u>Résultats réels</u>:

La quantité de produit double après l’ajout d’un produit au panier à partir de [!UICONTROL Product Grid].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
