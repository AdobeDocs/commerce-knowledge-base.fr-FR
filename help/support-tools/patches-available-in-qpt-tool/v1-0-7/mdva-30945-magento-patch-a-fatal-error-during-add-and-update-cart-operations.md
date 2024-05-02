---
title: 'MDVA-30945 : une erreur fatale lors des opérations d’ajout et de mise à jour de panier'
description: Le correctif MDVA-30945 corrige le problème en raison duquel vous recevez une erreur fatale *Appelez à une fonction membre getValue() sur null dans CartItemProcessor.php* configurable dans le module-produit lors de la mise à jour des paniers. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945 : erreur fatale lors des opérations d’ajout et de mise à jour de panier

Le correctif MDVA-30945 corrige le problème qui entraînait une erreur fatale. *Appel à une fonction membre getValue() sur null dans le module-configurable-product CartItemProcessor.php* lors de la mise à jour des paniers. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.7 est installée. Le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur PHP fatale après la mise à jour des produits du panier dans l’Admin.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur de Commerce, créez un produit configurable sans options.
1. Ajoutez-le au panier sur le storefront.
1. Revenez à Admin, ajoutez des options configurables au produit et enregistrez les modifications.
1. Actualisez la page du panier sur le storefront.

<u>Résultats attendus</u>:

Sur la page Panier, le message de validation suivant s’affiche : *Certains des produits ci-dessous ne disposent pas de toutes les options requises.*.

<u>Résultats réels</u>:

La page Panier est vide. Dans le PHP `error.log`, l’erreur suivante est consignée : *Exception non interceptée &quot;Error&quot; avec le message &quot;Call to a member function getValue() on null&quot; dans vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
