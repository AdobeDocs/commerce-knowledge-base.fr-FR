---
title: "MDVA-40488 : produits configurables avec des produits enfants en rupture de stock ne s’affichant pas dans la plage de prix correcte"
description: Le correctif MDVA-40488 résout le problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichent pas dans la plage de prix correcte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID de correctif est MDVA-40488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488 : produits configurables avec des produits enfants en rupture de stock ne s’affichant pas dans la plage de prix correcte

Le correctif MDVA-40488 résout le problème en raison duquel les produits configurables avec des produits enfants en rupture de stock ne s’affichent pas dans la plage de prix correcte. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID de correctif est MDVA-40488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables avec des produits enfants en rupture de stock ne sont pas affichés dans la plage de prix correcte.

<u>Conditions préalables</u> :

Accédez à Commerce Admin > **stores** > **configuration** > **catalogue** > **Inventaire** > **options de stock** et définissez la configuration **Afficher les produits en rupture de stock** sur *Oui*.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec deux produits associés. Par exemple : produits simples rouges et bruns.
1. Définissez l’inventaire du produit simple Rouge, et l’état du stock sur *In Stock*, puis définissez l’état Activer le produit sur *Non*.
1. Définissez l’inventaire du produit Brun simple, puis définissez l’état Activer le produit sur *Oui*.
1. Assurez-vous que le statut du produit configurable Stock est *En stock*.
1. Définissez l’inventaire du produit Brun simple sur 0 et l’état du stock sur *Rupture de stock*.
1. À ce stade, le statut du produit configurable Stock est toujours *En stock*.
1. Effectuez la réindexation.
1. Vérifiez les `min_price` et `max_price` pour le produit configurable dans la table `catalog_product_index_price` DB. Les deux valeurs sont définies sur 0.
1. Mais si nous définissons le statut du stock configurable sur *En rupture de stock* et que nous réindexons, nous pouvons alors voir les valeurs `min_price` et `max_price` non nulles du produit configurable.

<u>Résultats attendus</u> :

Si tous les produits enfants sont *En rupture de stock* et que le produit configurable lui-même est également *En rupture de stock*, le prix est calculé en utilisant tous les produits enfants.

<u>Résultats réels</u> :

Les valeurs `min_price` et `max_price` du produit configurable dans la table `catalog_product_index_price` DB sont définies sur 0 lorsque l’état du stock configurable est *En stock*, mais si c’est *En rupture de stock*, elles deviennent des valeurs non nulles.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
