---
title: 'MDVA-41229 : Images disponibles sur le serveur principal non affichées en front-end après l’importation de produits configurables'
description: Le correctif MDVA-41229 résout le problème en raison duquel les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-41229. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229 : Les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables

Le correctif MDVA-41229 résout le problème en raison duquel les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.12 est installée. L’ID de correctif est MDVA-41229. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2-p2 et 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables.

<u>Étapes à reproduire</u>:

1. Installez une Adobe Commerce propre.
1. Ajoutez un attribut personnalisé en accédant à **Magasins** > **Attributs** > **Produit** > **Ajouter un nouvel attribut** avec les paramètres ci-dessous :
   * Propriétés :
      * Propriétés d’attribut :
         * Libellé par défaut : Définir la taille
         * Type d’entrée de catalogue pour le propriétaire du magasin : nuance de texte
         * Valeurs requises : Non
         * Mettre à jour l’image d’aperçu du produit : Oui
      * Gérer l’échantillon (valeurs de votre attribut) :

        | Is Default | Echantillon d’administration | Description de l’administrateur | Échantillon d’affichage de magasin par défaut | Description de la vue de magasin par défaut |
        |---|---|---|---|---|
        | non | 4 | 4 | 4 | 4 |
        | non | 24 | 24 | 24 | 24 |
        | non | 30 | 30 | 30 | 30 |
        | non | 60 | 60 | 60 | 60 |
        | non | 68 | 68 | 68 | 68 |
      * Propriétés d’attribut avancées :
         * Code d’attribut : set_size
         * Portée : globale
         * Valeur unique : non
         * Validation d’entrée pour le propriétaire du magasin : aucune
         * Ajouter aux options de colonne : Non
         * Utiliser dans les options de filtre : Non
   * Gérer les étiquettes :
      * Gestion des titres (taille, couleur, etc.)
         * Affichage de magasin par défaut : définir la taille
   * Propriétés Storefront :
      * Utiliser dans la recherche : Oui
      * Poids de recherche : 1
      * Visible dans la recherche avancée : Non
      * Comparable sur Storefront : Oui
      * Utilisation dans la navigation par couches : filtrable (avec résultats)
      * Utiliser dans la navigation par couches des résultats de recherche : Oui
      * Utilisation pour les conditions de règle promotionnelle : Non
      * Visible sur les pages de catalogue sur Storefront : Oui
      * Utilisé dans la liste des produits : Oui
      * Utilisé pour le tri dans la liste des produits : Non
1. Ajoutez cet attribut au jeu d’attributs par défaut dans le groupe Détails du produit (**Magasins** > **Attributs** > **Jeu d’attributs**).
1. Téléchargez les images définies dans le dossier var dans le répertoire racine Adobe Commerce.
1. Accédez à **Système** > **Transfert de données** > et importez le fichier à l’aide des options suivantes :
   * Paramètres d’importation :
      * Type d’entité : Produits
   * Comportement d’importation :
      * Comportement d’importation : ajout/mise à jour
      * Stratégie de validation : Arrêter en cas d’erreur
      * Nombre d’erreurs autorisées : 1
      * Séparateur de champ : `;`
      * Séparateur de valeurs multiples : `,`
      * Constante de valeur d’attribut : EMPTYVALUE
      * Enfermement Champs : non coché
   * Fichier à importer :
      * Sélectionner un fichier à importer
      * Images File Directory : laissez-le vide
1. Accédez à storefront pour `/product-set.html` et basculez entre différentes tailles de jeu. Pour la Taille de la visionneuse 24, il n’y aura pas de galerie.

<u>Résultats attendus</u>:

La galerie de tous les produits simples d’un produit configurable est visible avec toutes les images associées.

<u>Résultats réels</u>:

Il n&#39;y a pas de galerie pour les produits.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
