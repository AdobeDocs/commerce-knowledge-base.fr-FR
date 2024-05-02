---
title: 'MDVA-40609 : données des produits désactivées absentes de la table cataloginventory_stock_status'
description: Le correctif MDVA-40609 résout le problème en raison duquel les données des produits désactivés ne s’affichent pas dans la table d’index `cataloginventory_stock_status`, ce qui entraîne l’affichage de quantités de produits incorrectes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 est installé. L’ID de correctif est MDVA-40609. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609 : Désactivation des données de produits absentes dans la table cataloginventory_stock_status

Le correctif MDVA-40609 résout le problème en raison duquel les données des produits désactivés ne s’affichent pas dans la variable `cataloginventory_stock_status` table d’index affichant des quantités de produits incorrectes. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.6 est installée. L’ID de correctif est MDVA-40609. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données des produits désactivés ne s’affichent pas dans la variable `cataloginventory_stock_status` table d’index affichant des quantités de produits incorrectes.

<u>Conditions préalables</u>:

Le module Inventaire est installé.

<u>Étapes à reproduire</u>:

1. Configurez deux sites web avec des magasins et des vues de magasin.
1. Créez une source et un stock supplémentaires.
1. Ajoutez un produit simple :
   * Définir l’option Activer le produit *Non*.
   * Attribuez deux sources avec État de l’élément source = En stock et Qté supérieur à zéro.
1. Enregistrez le produit.
1. Vérifiez les **Quantité vendable de produit** .

<u>Résultats attendus</u>:

Les deux stocks ont des valeurs saisies supérieures à zéro.

<u>Résultats réels</u>:

Un stock a une valeur nulle.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
