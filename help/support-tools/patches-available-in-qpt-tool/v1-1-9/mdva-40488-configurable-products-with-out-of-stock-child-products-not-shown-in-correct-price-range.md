---
title: "MDVA-40488 : produits configurables avec des produits enfants en rupture de stock ne s’affichant pas dans la plage de prix correcte"
description: Le correctif MDVA-40488 résout le problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichent pas dans la plage de prix correcte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID de correctif est MDVA-40488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488 : produits configurables avec des produits enfants en rupture de stock ne s’affichant pas dans la plage de prix correcte

Le correctif MDVA-40488 résout le problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichent pas dans la plage de prix correcte. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.9 est installée. L’ID de correctif est MDVA-40488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables avec des produits enfants en rupture de stock ne sont pas affichés dans la plage de prix correcte.

<u>Conditions préalables</u>:

Accédez à Administration Commerce > **stores** > **configuration** > **catalogue** > **Inventaire** > **options de stock** et défini **Afficher les produits en rupture de stock** configuration à *Oui*.

<u>Étapes à reproduire</u>:

1. Créez un produit configurable avec deux produits associés. Par exemple : produits simples rouges et bruns.
1. Définissez l’inventaire du produit simple Rouge et l’état du stock sur *En stock*, puis définissez l’état Activer le produit sur *Non*.
1. Définissez l’inventaire du produit Brun simple, puis l’état Activer le produit sur *Oui*.
1. Assurez-vous que l’état de stock configurable du produit est *En stock*.
1. Définissez l’inventaire du produit Brun simple sur 0 et l’état du stock sur 0. *En rupture de stock*.
1. À ce stade, le statut du stock de produit configurable reste *En stock*.
1. Effectuez la réindexation.
1. Vérifiez les `min_price` et `max_price` pour le produit configurable dans la variable `catalog_product_index_price` Table DB : les deux valeurs sont définies sur 0.
1. Mais si nous définissons l’état du stock configurable sur *En rupture de stock* et réindexer, puis nous pouvons voir non-zéro `min_price` et `max_price` des valeurs du produit configurable.

<u>Résultats attendus</u>:

Si tous les produits enfants sont *En rupture de stock* et le produit configurable lui-même est également *En rupture de stock*, le prix est calculé à l’aide de tous les produits enfants.

<u>Résultats réels</u>:

La variable `min_price` et `max_price` valeurs du produit configurable dans la variable `catalog_product_index_price` Le tableau DB est défini sur 0 lorsque l’état du stock configurable est *En stock*, mais si *En rupture de stock* elles deviennent des valeurs non nulles.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
