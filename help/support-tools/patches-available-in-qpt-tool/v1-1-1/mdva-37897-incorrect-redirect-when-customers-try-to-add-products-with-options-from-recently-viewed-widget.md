---
title: 'MDVA-37897 : Redirection incorrecte lors de l’ajout de produits à partir de Récemment consultés'
description: Le correctif MDVA-37897 résout le problème d’une redirection incorrecte lorsque les utilisateurs tentent d’ajouter des produits avec des options du widget Récemment consultés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 est installé. L’ID de correctif est MDVA-37897. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897 : Redirection incorrecte lors de l’ajout de produits issus de la catégorie Récemment consultés

Le correctif MDVA-37897 résout le problème d’une redirection incorrecte lorsque les utilisateurs tentent d’ajouter des produits avec des options du widget Récemment consultés. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 est installé. L’ID de correctif est MDVA-37897. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un utilisateur tente d’ajouter un produit de la section Récemment consultés qui doit comporter les options requises pour être sélectionné, il est redirigé vers la page de liste de produits au lieu de la page de détails des produits.

<u>Étapes à reproduire</u> :

1. Créez un produit simple avec des options personnalisables (Type : bouton radio).
1. Configurez le widget Récemment consultés pour afficher les produits.
1. Visitez les produits qui disposent d’options personnalisables afin qu’ils s’affichent dans le widget Récemment consultés .
1. Cliquez sur **Ajouter au panier** sur l’un des produits du widget Récemment consultés.

<u>Résultats attendus</u> :

Vous êtes redirigé vers la page des détails du produit pour choisir les options.

<u>Résultats réels</u> :

Vous êtes redirigé vers la page de liste de produits.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce on-premise : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur notre infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
