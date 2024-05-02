---
title: "MDVA-29787 : les produits associés ne sont pas affichés"
description: Le correctif MDVA-29787 résout le problème en raison duquel **Produits associés** ne s’affichent pas sur une interface de magasin Adobe Commerce. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. L’ID de correctif est MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787 : les produits associés ne sont pas affichés

Le correctif MDVA-29787 résout le problème où **Produits associés** ne s’affichent pas sur un front-end de magasin Adobe Commerce. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.6 est installée. L’ID de correctif est MDVA-29787.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.3.

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.0.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de ciblage pour **Produits associés** ne fonctionne pas lorsque &quot;*est l’un des*&quot; condition est utilisée pour **Produits à afficher** dans l’administrateur de Commerce.

>[!NOTE]
>
>Remarque : Ce correctif ne corrige pas les règles de ciblage existantes. Vous devez recréer des règles de ciblage existantes.

<u>Étapes à reproduire</u>:

1. Créer **Nouvel attribut** (Exemple : Test\_Attr).
   * Définir **Type d’entrée de catalogue pour le propriétaire du magasin** = *Texte.*
   * Dans **Propriétés Storefront**, définit **Utilisation pour les conditions des règles de promotion** = *Oui*.
1. Créer **Nouveau jeu d’attributs** (Exemple : Test\_Set).
1. Ajoutez la variable **Nouvel attribut** à la fonction **Nouveau jeu d’attributs** (Exemple : ajoutez l’attribut &quot;Test\_Attr&quot; au jeu d’attributs &quot;Test\_Set&quot;).
1. Créez trois produits. Pour l’exemple, ils sont définis comme suit :
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Product3, Test\_Attr = 701644329389M
1. Créer une cible **Règle** (**Marketing**   > **Règles de produit connexes** et cliquez sur le bouton **Ajouter une règle** ). avec les paramètres :
   * **Appliquer à** = *Produits associés*
   * **Produits à faire correspondre**
   * Définir le nouvel attribut que vous avez créé **in** **Étape 1 ci-dessus** pour être l’attribut de Product1 (par exemple : Test\_Attr = MAGT2NA\_Test3).
   * **Produits à afficher** = Attributs des deux autres produits (par exemple : attributs 24-MB02 et 701644329389M).
1. Enregistrez le **Règle**.
1. Exécutez une réindexation, si nécessaire.
1. Effacez le cache.
1. Ouvrez Product1 sur le front-end.

<u>Résultats attendus</u>:

Les produits associés sont présents.

<u>Résultats réels</u>:

Les produits associés sont manquants.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
