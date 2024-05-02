---
title: 'Correctif MDVA-31224 : la réindexation des prix du produit prend trop de temps'
description: Le correctif MDVA-31224 résout le problème lorsque la réindexation des prix du produit prend trop de temps à se terminer ou ne jamais se terminer. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 est installé.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Correctif MDVA-31224 : la réindexation des prix des produits prend trop de temps.

Le correctif MDVA-31224 résout le problème lorsque la réindexation des prix du produit prend trop de temps à se terminer ou ne jamais se terminer. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 est installé.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.3.
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation des prix du produit prend trop de temps pour être terminée ou jamais.

<u>Étapes à reproduire :</u>

1. Créez 6 000 produits regroupés avec 15 options.
1. Créez 1 produit fourni avec 30 options.
1. Exécutez la réindexation de prix à partir de l’interface de ligne de commande :     `bin/magento indexer:reindex catalog_product_price`

<u>Résultats attendus :</u>

La réindexation des prix du produit prend 1,5 heure ou plus.

<u>Résultats réels :</u>

La réindexation des prix du produit prend un court temps (une ou deux minutes).

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
