---
title: "MDVA-30107 : le sélecteur de magasin ne fonctionne pas comme prévu"
description: Le correctif MDVA-30107 résout le problème en raison duquel le sélecteur de magasin ne fonctionne pas comme prévu si différentes URL de base sont utilisées pour les vues de magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé.
exl-id: feaef9ed-615f-4a0a-a7c5-1833f993d27f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-30107 : le sélecteur de magasin ne fonctionne pas comme prévu.

Le correctif MDVA-30107 résout le problème en raison duquel le sélecteur de magasin ne fonctionne pas comme prévu si différentes URL de base sont utilisées pour les vues de magasin. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé.

## Produits et versions concernés

* Adobe Commerce On-Premise 2.3.0 - 2.3.5.x
* Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.3.5.x

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un utilisateur bascule entre les magasins à l’aide du sélecteur de magasin, la demande échoue si le magasin cible a une URL de base différente.

<u>Étapes à reproduire</u> :

1. Créez plusieurs magasins avec des URL de base différentes.
1. Accédez à une page de catégorie sur une vitrine de l’un de ces magasins.
1. Essayez de basculer vers l’autre magasin à l’aide du sélecteur de magasin.

<u>Résultats attendus</u> :

Vous êtes redirigé vers une page similaire de l’autre magasin.

<u>Résultats réels</u> :

Vous êtes redirigé vers la page d’accueil du même magasin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
