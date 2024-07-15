---
title: "MDVA-31021 : importation et exportation lentes si de nombreuses options de produit"
description: Le correctif MDVA-31021 résout le problème lorsque l’importation/exportation prend plus de temps que prévu avec un grand nombre d’options de produit. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021 : importation et exportation lentes si de nombreuses options de produits

Le correctif MDVA-31021 résout le problème lorsque l’importation/exportation prend plus de temps que prévu avec un grand nombre d’options de produit. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Si la table `catalog_product_option` contient plus de 100 000 enregistrements, la validation du fichier de fonction d&#39;import/export prend plus de temps que prévu. Avant l’importation/exportation, pour vérifier la validation des options, Adobe Commerce charge les options de produit pour tous les produits existants.

<u>Conditions préalables</u> :

Magasin Adobe Commerce avec 5 000 produits avec des options personnalisées. Chaque produit doit avoir au moins quatre options personnalisées avec au moins deux options parmi lesquelles choisir, de sorte qu’il y ait 100 000 enregistrements dans la table `catalog_product_option`.

<u>Étapes à reproduire</u> :

1. Pour un exemple **Import** : créez un fichier d’importation CSV avec l’un des SKU de l’administrateur Commerce.
1. Ajoutez quatre options personnalisées au fichier d’importation CSV.
1. Essayez d’importer le fichier CSV à partir de l’administrateur Commerce.

<u>Résultats attendus</u> :

La fonction Importer ou Exporter se termine comme prévu. La validation prend moins de 10 secondes pour se terminer avec un produit.

<u>Résultats réels</u> :

La fonction Importer ou Exporter dure plus longtemps que prévu. La validation prend plus de 10 secondes pour se terminer avec un seul produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
