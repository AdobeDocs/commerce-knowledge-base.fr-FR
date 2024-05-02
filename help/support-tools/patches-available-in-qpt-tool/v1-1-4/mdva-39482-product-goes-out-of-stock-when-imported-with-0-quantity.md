---
title: '"MDVA-39482 : le produit est en rupture de stock s’il est importé avec une quantité "0" avec des commandes en arrière-plan activées"'
description: Le MDVA-39482 corrige le problème de rupture de stock du produit s’il est importé avec une quantité "0" lorsque les MSI et les commandes de sauvegarde sont activés et que le seuil d’rupture de stock est défini sur une valeur moins élevée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 est installé. L’ID de correctif est MDVA-39482. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482 : le produit est en rupture de stock s’il est importé avec une quantité &quot;0&quot; avec des commandes en arrière-plan activées.

Le MDVA-39482 corrige le problème de rupture de stock du produit s’il est importé avec une quantité &quot;0&quot; lorsque les MSI et les commandes de sauvegarde sont activés et que le seuil d’rupture de stock est défini sur une valeur moins élevée. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.1.4 est installée. L’ID de correctif est MDVA-39482. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit est en rupture de stock s’il est importé avec une quantité &quot;0&quot; lorsque les MSI et les commandes en arrière-plan sont activés et que le seuil en rupture de stock est défini sur une valeur moins élevée.

<u>Conditions préalables</u>:

1. Les MSI et les exemples de données doivent être installés.
1. Accédez à **Magasins** > **Configurations** > **Catalogue** > **Inventaire**:
   * Définissez les commandes d’arrière-plan sur &quot;Autoriser une valeur inférieure à 0&quot;.
   * Définissez le seuil en rupture de stock sur &quot;-10&quot;.

<u>Étapes à reproduire</u>:

1. Vérifiez que le SKU est **En stock** et a une quantité **24 Mo01**.
1. Importez le fichier CSV de la source Stock. Veillez à sélectionner &quot;Sources de stock&quot; dans le type d’entité :

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Vérifiez l’état des stocks du produit une fois que les sources de stock ont été importées.

<u>Résultats attendus</u>:

24 Mo01 est **En stock** à Storefront.

<u>Résultats réels</u>:

24 Mo01 est **En rupture de stock** à Storefront.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
