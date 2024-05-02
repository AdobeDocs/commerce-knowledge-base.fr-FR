---
title: "MDVA-33168 : le point de terminaison asynchrone de l’API annule la définition du prix spécial"
description: Le correctif MDVA-33168 corrige le problème en raison duquel l’utilisation du point de terminaison asynchrone de l’API pour mettre à jour un attribut de produit annule la définition d’un prix spécial.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168 : le point de terminaison asynchrone de l’API annule le prix spécial.

Le correctif MDVA-33168 corrige le problème en raison duquel l’utilisation du point de terminaison asynchrone de l’API pour mettre à jour un attribut de produit annule la définition d’un prix spécial.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.20 est installée. L’ID de correctif est MDVA-33168. Veuillez noter que le problème devrait être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.3-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.3 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Créez deux sites web avec des magasins.
1. Accédez à **Magasins > Configurations > Catalogue > Catalogue > Prix > Catalogue** et définissez **Étendue du prix** = *Site Web*.
1. Créez un *text-type* attribut de produit. Conservez toutes les options par défaut.
1. Ajoutez l’attribut créé au jeu d’attributs par défaut.
1. Créez un produit simple à utiliser avec un produit groupé.
1. Créez un produit groupé avec les options d’exemple suivantes :
   * **Activer le produit** = *Oui*.
   * **Jeu d’attributs** = *Par défaut*.
   * **Nom du produit** = *bundle-1*.
   * **SKU** = *bundle-1*.
   * **SKU dynamique** = *Oui*.
   * **Prix** = *100,00 $*.
   * **Classe fiscale** = *Biens taxables*.
   * **État du stock** = *En stock*.
1. Sous **Éléments groupés**, définissez les options Exemple suivantes :
   * **Ship Bundle Items** = *Ensemble*.
   * **Titre de l’option** = *test*, **Type d’entrée** = *Boutons radio*, **Obligatoire** case à cocher = *vérifié*.
   * **Is Default** case à cocher = *unchecked*.
   * **Nom** = *simple-100*.
   * **SKU** = *simple-100*.
   * **Prix** = *100,00*.
   * **Type de prix** = *Fixe*.
   * **Quantité par défaut** = *1*.
   * **Défini par l’utilisateur** case à cocher = *unchecked*.
1. Basculez la portée vers le magasin autre que le magasin par défaut et définissez le prix spécial. (Exemple : sur la page **Tarifs avancés** page, définir **Prix spécial** = *4 %*, et **Affichage du prix** = *Plage de prix*.)
1. Mettez à jour le nouvel attribut uniquement dans la portée de magasin autre que celle par défaut, comme dans cet exemple :

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Résultats attendus</u>:

Les autres valeurs d’attribut restent les mêmes lors de la mise à jour d’un attribut de produit à l’aide de l’API REST asynchrone, comme prévu.

<u>Résultats réels</u>:

Le prix spécial, qui a été défini à l’aide de l’API REST asynchrone sous la portée du magasin, est supprimé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
