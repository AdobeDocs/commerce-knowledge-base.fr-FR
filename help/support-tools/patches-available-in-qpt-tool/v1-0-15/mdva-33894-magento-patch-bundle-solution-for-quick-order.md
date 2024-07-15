---
title: 'Correctif MDVA-33894 : solution de regroupement pour commande rapide'
description: Le correctif MDVA-33894 corrige plusieurs problèmes pour la fonctionnalité de commande rapide, notamment l’ajout et la suppression de plusieurs produits et le respect de la casse des SKU. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Correctif MDVA-33894 : solution de regroupement pour commande rapide

Le correctif MDVA-33894 corrige plusieurs problèmes pour la fonctionnalité de commande rapide, notamment l’ajout et la suppression de plusieurs produits et le respect de la casse des SKU. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.4.0-2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif MDVA-33894 est une solution de regroupement avec des correctifs pour les problèmes suivants :

* La fonctionnalité **Mon compte** > **Ordre de tri par SKU** est sensible à la casse : si vous saisissez un SKU valide mais que la casse n’est pas correcte (majuscules au lieu de minuscules, etc.), Adobe Commerce renvoie une erreur.
* Lorsqu’un acheteur utilise la commande rapide pour ajouter plusieurs produits à son panier et tente de supprimer un produit, le produit n’est pas supprimé.
* Problèmes de respect de la casse lors de l’ajout de plusieurs SKU à une commande en bloc.
* Problème de mise en cache de la page de commande rapide avec les SKU précédemment saisis.
* La quantité de commande rapide n’est pas répercutée dans le panier.
* La duplication des SKU n’est pas validée correctement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
