---
title: "Correctif MDVA-28202 : les produits en rupture de stock ne se filtrent pas correctement"
description: Le correctif MDVA-28202 résout le problème en raison duquel les produits en rupture de stock ne sont pas correctement filtrés à l’aide du filtre **Price** sur un serveur frontal de magasin Adobe Commerce. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 est installé.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Correctif MDVA-28202 : les produits en rupture de stock ne sont pas correctement filtrés.

Le correctif MDVA-28202 résout le problème en raison duquel les produits en rupture de stock ne sont pas correctement filtrés à l’aide de **Prix** filtrer sur un front-end de magasin Adobe Commerce. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 est installé.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.5-p1.
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4 à 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits en rupture de stock ne sont pas correctement filtrés à l’aide de **Prix** filtre dans l’administrateur Commerce.

<u>Condition préalable requise :</u>

* Définir **Afficher les produits en rupture de stock** = &quot;*Oui*&quot; sous **Magasins > Configuration > CATALOGUE > Inventaire > Options d’inventaire**.

<u>Étapes à reproduire :</u>

1. Créez un produit configurable avec deux produits simples (par exemple : set **Prix** = *1 500 $*).
1. Les deux produits simples doivent être &quot;en rupture de stock&quot; lors de la création du produit configurable.
1. Attribuez ce produit configurable à une catégorie.
1. Réindexation et vérification `catalog_product_index_price` table utilisant l’identifiant d’entité du produit configurable ci-dessus.
1. Économisez tous les prix du produit = *0 $*.
1. Chargez la catégorie et vérifiez la disponibilité du produit.
1. Ouvrez le **Prix** à partir de la navigation par couches.
1. Notez que la variable **Prix** Le filtre possède une option de &quot; *0,00 $ - 9,99 $* &quot;.
1. Cliquez sur ce lien ci-dessus **Prix** et définissez l’option **Prix** = *1 500 $* et vous obtiendrez le produit configurable que nous avons créé ci-dessus.

<u>Résultat attendu :</u>

Le produit est filtré selon la plage de prix correcte, comme prévu.

<u>Résultat réel :</u>

Le produit tombe sous un filtre de plage de prix incorrect.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Application de correctifs à l’aide de l’outil Correctifs de qualité](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .

Pour en savoir plus sur les produits configurables, consultez cet article dans notre documentation destinée aux développeurs : [Tutoriel sur la création d’un produit configurable](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) dans notre documentation destinée aux développeurs.
