---
title: 'Correctif MDVA-31759 : l’importation CSV ignore les mises à jour des attributs'
description: Le correctif MDVA-31759 corrige le problème en raison duquel l’importation CSV ignorait les attributs supplémentaires avec les types *Liste déroulante* et *Zone de texte*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Correctif MDVA-31759 : l’importation CSV ignore les mises à jour des attributs.

Le correctif MDVA-31759 corrige le problème en raison duquel l’importation CSV ignore les attributs supplémentaires avec *Liste déroulante* et *Zone de texte* types. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.9 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation CSV ignore les attributs supplémentaires avec *Liste déroulante* et *Zone de texte* types.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur Commerce.
1. Créez un attribut de produit avec la configuration suivante :
   * **Libellé par défaut**: *G003*
   * **Type d’entrée de catalogue pour le propriétaire du magasin**: *Zone de texte* ou *Liste déroulante*
   * **Code d’attribut**: *G003*
   * **Portée**: *Global*
1. Ajoutez l’attribut ci-dessus au jeu d’attributs par défaut.
1. Créez un produit avec le jeu d’attributs par défaut et spécifiez une valeur pour le nouvel attribut.
1. Exportez le produit au format CSV.
1. Mettez à jour la valeur d’attribut dans la variable **additional\_attributes** colonne .
1. Importez le fichier CSV mis à jour.

<u>Résultats attendus</u>:

La valeur de l’attribut G003 est mise à jour.

<u>Résultats réels</u>:

La valeur de l’attribut G003 n’est pas mise à jour.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
