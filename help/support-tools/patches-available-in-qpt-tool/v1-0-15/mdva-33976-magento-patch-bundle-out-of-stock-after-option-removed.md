---
title: 'MDVA-33976 patch : lot en rupture de stock après suppression de l’option'
description: Le correctif MDVA-33976 corrige le problème qui entraînait l’affichage d’un produit en rupture de stock comme produit en rupture de stock après la suppression de l’une de ses options dans Admin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Correctif MDVA-33976 : lot en rupture de stock après suppression de l’option

Le correctif MDVA-33976 corrige le problème qui entraînait l’affichage d’un produit en rupture de stock comme produit en rupture de stock après la suppression de l’une de ses options dans Admin. Ce correctif est disponible lorsque la variable [Outil de correctifs de qualité (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.3

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0-2.3.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Ouvrez un produit en bundle dans l’administrateur Commerce.
1. Supprimez l’une des options de produit du lot.
1. Enregistrez les modifications.
1. Ouvrez le produit sur le storefront.

<u>Résultat attendu</u>:

L’état du stock de produit du lot est mis à jour en fonction de l’état du stock de produit enfant.

<u>Résultat réel</u>:

Le produit du lot est affiché en rupture de stock, quel que soit le statut du produit enfant.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
