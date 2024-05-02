---
title: "MDVA-30963 : le filtre de recherche de produit d’administration ne fonctionne pas comme prévu"
description: Le correctif MDVA-30963 résout le problème en raison duquel l’administrateur Commerce et le filtre de recherche de produits ne fonctionnent pas comme prévu. Les valeurs qui sont remplacées dans une portée de vue de magasin sont également prises en compte lors du filtrage sur **Vue de magasin** portée de vue de magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963 : le filtre de recherche de produits d’administration ne fonctionne pas comme prévu

Le correctif MDVA-30963 résout le problème en raison duquel l’administrateur Commerce et le filtre de recherche de produits ne fonctionnent pas comme prévu. Les valeurs qui sont remplacées dans une portée de vue de magasin sont également prises en compte lors du filtrage sur **Toutes les vues de magasin** portée de la vue de magasin. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.8 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Définir **Magasins** > **Configuration** > **Catalogue** > **Catalogue** > **Prix** > **Portée du prix du catalogue** = *Site Web*.
1. Créez deux sites web ayant deux devises différentes (par exemple, le site web par défaut est un magasin indien \[roupie ₹\], et le second est le magasin américain \[dollar $\]).
1. Définissez les **Devise de base**, **Devise d’affichage par défaut**, et **Devises autorisées**:
   * **Configuration par défaut** = *Dollar US (par défaut)*
   * **Site web principal** = *Inde : roupie*
   * **WebsiteUS** = **Utiliser la valeur par défaut** = *Dollar US*
1. Définir **Magasins** > **Taux de change** = *1:1*.
1. Créez un produit de test simple affecté aux deux sites web avec les prix suivants :
   * **Prix par défaut** = **Prix du site web américain** = *123 USD*
   * **Prix du site web principal** = *321 roupies*
1. Créez un utilisateur sous-administrateur ayant uniquement accès au magasin E.U.
1. Positionnez-vous sur le storefront des Etats-Unis et positionnez un produit dans le panier (par exemple : *Prix 123 USD*).
1. Connectez-vous à l’administrateur avec le sous-administrateur que vous venez de créer (exemple : *Administration des États-Unis uniquement*).
1. Accédez à **Rapports** > **Produits dans le panier**.

<u>Résultats attendus</u>:

Lors du filtrage dans la variable **Toutes les vues de magasin** périmètre de la vue de magasin, le filtrage des produits doit obtenir la valeur définie dans cette portée particulière.

<u>Résultats réels</u>:

Les valeurs remplacées dans une portée de vue de magasin sont également prises en compte lors du filtrage sur la portée de vue de magasin &quot;Toutes les vues de magasin&quot;.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
