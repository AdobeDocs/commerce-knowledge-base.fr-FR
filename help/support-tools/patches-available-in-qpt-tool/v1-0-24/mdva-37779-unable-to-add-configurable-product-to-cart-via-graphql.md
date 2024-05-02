---
title: 'MDVA-37779 : impossible d’ajouter un produit configurable au panier via GraphQL'
description: Le correctif Adobe Commerce MDVA-3779 résout le problème où il est impossible d’ajouter un produit configurable au panier lorsque l’identifiant du site web n’est pas égal à l’identifiant du magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 est installé. L’ID de correctif est MDVA-37779. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779 : impossible d’ajouter un produit configurable au panier via GraphQL

Le correctif Adobe Commerce MDVA-3779 résout le problème où il est impossible d’ajouter un produit configurable au panier lorsque l’identifiant du site web n’est pas égal à l’identifiant du magasin. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.24 est installée. L’ID de correctif est MDVA-37779. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il est impossible d’ajouter un produit configurable au panier lorsque l’identifiant du site web n’est pas égal à l’identifiant du magasin.

<u>Conditions préalables</u>:

disposer d’un deuxième site web, d’une deuxième vue de magasin et d’un deuxième affichage de magasin où l’ID de site web n’est pas égal à l’ID de magasin ;

<u>Étapes à reproduire</u>:

1. Création d’un panier vide à l’aide d’une mutation GraphQl `createEmptyCart`.
1. Essayez d’ajouter un produit configurable au panier à l’aide de la variable `addConfigurableProductsToCart` mutation.

<u>Résultats attendus</u>:

Produit ajouté au panier.

<u>Résultats réels</u>:

Obtenir une erreur : *Impossible d’ajouter le produit avec le SKU xxxx au panier : le site web avec l’ID 3 demandé est introuvable. Vérifiez le site web et réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.


## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
