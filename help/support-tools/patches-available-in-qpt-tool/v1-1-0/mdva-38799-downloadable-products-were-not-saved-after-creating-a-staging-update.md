---
title: "MDVA-38799 : produits téléchargeables non enregistrés après la création d’une mise à jour intermédiaire"
description: Le correctif MDVA-38799 résout le problème en raison duquel les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour intermédiaire. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 est installé. L’ID de correctif est MDVA-38799. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799 : produits téléchargeables non enregistrés après la création d’une mise à jour intermédiaire

Le correctif MDVA-38799 résout le problème en raison duquel les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour intermédiaire. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.0 est installée. L’ID de correctif est MDVA-38799. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour intermédiaire. Les utilisateurs reçoivent le message d’erreur : *L’exemple téléchargeable n’est pas lié au produit. Vérifier le lien et réessayer*.

<u>Étapes à reproduire</u>:

1. Accédez à **Catalogue** > **Produits**.
1. Cliquez sur la liste déroulante en regard de Ajouter un produit et sélectionnez Produit téléchargeable.
   * Renseignez le nom, le SKU, le prix et la quantité du produit.
1. Faites défiler jusqu’à la page d’informations téléchargeables.
1. Sous Exemples, cliquez sur **Ajouter un lien**.
   * Remplissez le titre, Télécharger le fichier (le type de fichier n’a pas d’importance).
1. Cliquez sur **Enregistrer**. Vous obtiendrez le message suivant : *Vous avez enregistré le produit.*.
1. Cliquez sur **Planifier une nouvelle mise à jour** en haut de la page.
   * Remplissez le Nom de mise à jour et indiquez une Date de début et une Date de fin légales.
1. Cliquez sur **Enregistrer** lors de la mise à jour intermédiaire.
1. Cliquez sur **Enregistrer** sur le produit.

<u>Résultats attendus</u>:

Le produit est enregistré sans erreur.

<u>Résultats réels</u>:

Le message d’erreur s’affiche : *L’exemple téléchargeable n’est pas lié au produit. Vérifier le lien et réessayer*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
