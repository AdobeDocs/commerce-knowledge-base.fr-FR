---
title: 'MDVA-42584 : statut du stock du produit configurable non mis à jour automatiquement'
description: Le correctif MDVA-42584 résout le problème en raison duquel l’état du stock du produit configurable n’est pas mis à jour automatiquement lorsque son produit simple est mis à jour. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-42584. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584 : statut du stock du produit configurable non mis à jour automatiquement

Le correctif MDVA-42584 résout le problème en raison duquel l’état du stock du produit configurable n’est pas mis à jour automatiquement lorsque son produit simple est mis à jour. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.10 est installée. L’ID de correctif est MDVA-42584. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état du stock du produit configurable dans le serveur principal n’est pas mis à jour automatiquement lorsque son produit simple est défini sur **En stock** via l’API ou l’importation.

<u>Conditions préalables</u>:

MSI installé.

<u>Étapes à reproduire</u>:

1. Créer un produit configurable, **InvCheck001**, avec deux options : **InvCheck001-M** et **InvCheck001-L**.
1. Les deux produits simples doivent avoir la quantité et ils doivent être **En stock** de sorte que le produit configurable soit également **En stock** dans le serveur principal.
1. Mettez à jour les produits simples et définissez Quantité sur **0** et État du stock sur **En rupture de stock**.
1. Actualisez le produit configurable et vérifiez que l’état du stock est mis à jour pour **En rupture de stock**.
1. Utilisez le point d’entrée API suivant et définissez le produit simple **InvCheck001-M** to **En stock** avec Quantité > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Accédez au serveur principal et vérifiez la quantité et l’état du stock du produit simple. **InvCheck001-M**. Il est mis à jour vers **En stock**.
1. Actualisez le produit configurable et vérifiez l’état du stock.

<u>Résultats attendus</u>:

État du stock du produit configurable **InvCheck001** dans le serveur principal est automatiquement mis à jour vers **En stock**.

<u>Résultats réels</u>:

L’état du stock du produit configurable reste **En rupture de stock**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
