---
title: '''MDVA-28763 : problèmes liés à la gestion des images de produits via l''API REST'''
description: Le correctif MDVA-28763 résout plusieurs problèmes liés à la gestion de la galerie multimédia à l’aide de l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. Les problèmes doivent être corrigés dans les versions ultérieures d’Adobe Commerce.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763 : problèmes liés à la gestion des images de produits via l&#39;API REST

Le correctif MDVA-28763 résout plusieurs problèmes liés à la gestion de la galerie multimédia à l’aide de l’API REST. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.5 est installée. Les problèmes doivent être résolus dans les versions ultérieures d’Adobe Commerce (voir les descriptions de problèmes dans [Problèmes](#issues).

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce On-Premise 2.3.2 - 2.3.3.x
* Adobe Commerce sur l’infrastructure cloud 2.3.2 - 2.3.3.x

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problèmes {#issues}

Le correctif MDVA-28763 comprend des correctifs pour les problèmes suivants liés à la galerie multimédia :

* Lors de l’utilisation de l’API REST pour mettre à jour des vidéos YouTube (`PUT rest/V1/products/ {SKU}`, Adobe Commerce affiche une miniature de la vidéo, mais le lecteur vidéo ne se charge pas lorsque vous cliquez sur le bouton &quot;Lecture&quot;. Planifié à corriger dans Adobe Commerce 2.3.6.
* `PUT /V1/products/:sku/media/:entryId` crée une nouvelle entrée plutôt que de la remplacer. Corrigé dans Adobe Commerce 2.3.5.
* Problèmes de suppression d’images de produit lorsque des produits sont affectés à plusieurs vues de magasin. Corrigé dans Adobe Commerce 2.3.4.
* Les vendeurs disposant de plusieurs sites web peuvent désormais utiliser REST pour créer et mettre à jour des produits tout en préservant l’héritage image-rôle. Auparavant, lorsqu’un commerçant utilisait REST pour créer et mettre à jour des produits et qu’un produit était mis à jour pour la vue de magasin, les rôles d’image par défaut étaient chargés et enregistrés pour cette vue de magasin. Par conséquent, les rôles d’image de vue de magasin ont cessé d’hériter de la portée par défaut après la mise à jour. Planifié à corriger dans Adobe Commerce 2.3.6.
* Attributs de média (image, miniature, etc.) valeurs dans les vues de magasin faisant référence à des images supprimées qui ne sont pas automatiquement nettoyées. Planifié à corriger dans Adobe Commerce 2.4.2.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
