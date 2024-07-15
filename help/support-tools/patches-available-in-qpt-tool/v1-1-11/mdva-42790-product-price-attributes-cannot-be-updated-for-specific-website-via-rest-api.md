---
title: 'MDVA-42790 : les attributs de prix du produit ne peuvent pas être mis à jour pour un site web spécifique via l’API REST'
description: Le correctif MDVA-42790 corrige le problème en raison duquel les utilisateurs ne sont pas en mesure de mettre à jour les attributs de prix de produit pour des sites web spécifiques via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé. L’ID de correctif est MDVA-42790. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: b9d80190-17d2-436f-86d5-33689b8224d4
feature: REST, Attributes, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-42790 : les attributs de prix de produit ne peuvent pas être mis à jour pour un site web spécifique via l’API REST.

Le correctif MDVA-42790 corrige le problème en raison duquel les utilisateurs ne sont pas en mesure de mettre à jour les attributs de prix de produit pour des sites web spécifiques via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé. L’ID de correctif est MDVA-42790. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas mettre à jour les attributs de prix de produit pour des sites web spécifiques via l’API REST.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur, accédez à **Magasins** > **Configuration** > **Catalogue** > **Prix** > et définissez **Portée du prix du catalogue** sur le site Web.
1. Mettez à jour le prix spécial d’un produit groupé à l’aide de l’API REST, `POST rest/V1/products/`.

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>Résultats attendus</u> :

Un prix spécial est mis à jour pour le produit fourni lorsque la **portée du prix du catalogue** est définie sur Site Web.

<u>Résultats réels</u> :

Le prix spécial n’est pas mis à jour pour le produit fourni lorsque la **portée du prix du catalogue** est définie sur Site Web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
