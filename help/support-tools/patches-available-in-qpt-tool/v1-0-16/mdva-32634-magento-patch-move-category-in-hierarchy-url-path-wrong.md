---
title: 'Correctif MDVA-32634 : déplacer la catégorie dans la hiérarchie url_path incorrect'
description: Le correctif MDVA-32634 résout le problème en raison duquel l’url\_path de la catégorie de catalogue ne change pas après le déplacement de la catégorie dans la hiérarchie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Correctif MDVA-32634 : la catégorie de déplacement dans la hiérarchie url_path est incorrecte

Le correctif MDVA-32634 résout le problème en raison duquel l’url\_path de la catégorie de catalogue ne change pas après le déplacement de la catégorie dans la hiérarchie. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.16 est installée. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.1 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le déplacement d’une catégorie de catalogue dans la hiérarchie génère un URL\_path incorrect. URL\_path de la catégorie affectée à la portée de magasin par défaut \[ **id:0** \] reste inchangé après le déplacement de la catégorie dans la hiérarchie.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur Commerce. Créez la structure de catégorie suivante sous la catégorie racine : move-cat sub-move-cat sub-move-cat2 new-cat-move
1. Vérifiez l’attribut \[ url\_path \] de la catégorie \[ id: 120 \] pour l’affectation de valeur dans la table \[ catalog\_category\_entity\_varchar \] à l’aide de la requête suivante :

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Cela devrait vous donner le résultat suivant :

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Les valeurs \[ url\_path \] ont été générées et affectées à la portée de tous les magasins \[ 0 \]. Ceci est correct par rapport à une instance sans B2B.
1. Accédez à la liste des catégories du serveur principal, faites glisser \[ move-cat \] et déposez-le dans \[ new-cat-move \]. La catégorie doit maintenant ressembler à : new-cat-move-move-cat sub-move-cat sub-move-cat2
1. Vérifiez la table \[ catalog\_category\_entity\_varchar \] à l’aide de la requête suivante :

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Résultats attendus</u>:

L’url\_path affecté à l’étendue de magasin \[ 0 \] doit également être mis à jour avec le nouveau chemin.

<u>Résultats réels</u>:

L’url\_path affecté à l’étendue de magasin \[ 0 \] reste inchangé, même s’il n’y a aucun chemin disponible après le déplacement. De nouvelles valeurs url\_path sont également créées pour chaque magasin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
