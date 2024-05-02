---
title: "MDVA-39181 : les règles de produit connexes affichent les produits de la catégorie non définie dans la règle"
description: Le correctif MDVA-39181 résout le problème en raison duquel les règles de produit associées affichent les produits d’une catégorie non définie dans la règle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-39181. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181 : les règles de produit connexes affichent les produits de la catégorie non définis dans la règle.

Le correctif MDVA-39181 résout le problème en raison duquel les règles de produit associées affichent les produits d’une catégorie non définie dans la règle. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.10 est installée. L’ID de correctif est MDVA-39181. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles de produit connexes affichent les produits des catégories qui ne sont pas définies dans la règle.

<u>Conditions préalables</u>:

Installez des exemples de données.

<u>Étapes à reproduire</u>:

1. Créez une marque d’attribut et ajoutez-la au **Principaux jeux d’attributs**.
1. Choisir **Josie**, **Augusta**, et **Ingrid** vestes à ajouter à la marque Kitty à partir de **Femmes** > **Principaux** > **Catégorie Jackets**.
1. Choisir **Beaumont**, **Hyperion**, et **Kenobi** vestes à ajouter à la marque Kitty à partir de **Hommes** > **Principaux** > **Catégorie de Jacket**.
1. Créez un produit associé avec :

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produits à faire correspondre :

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Produits à afficher :

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Ouvrez la SKU WJ04 à partir du front-end et vérifiez les produits associés.
1. Mettre à jour l’ID de catégorie depuis **Femmes** > **Principaux** > **Jackets** au cas où cela serait différent.

<u>Résultats attendus</u>:

Seuls les produits de la même marque et de la même catégorie enfant sont affichés dans les produits associés.

<u>Résultats réels</u>:

Les produits associés sont affichés pour la même marque mais à partir d’une catégorie parente aléatoire.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
