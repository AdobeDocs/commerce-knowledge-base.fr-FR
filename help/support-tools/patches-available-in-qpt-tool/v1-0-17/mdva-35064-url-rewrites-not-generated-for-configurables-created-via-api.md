---
title: 'MDVA-35064 : réécritures d’URL non générées pour les éléments configurables créés via l’API'
description: Le correctif MDVA-35064 corrige le problème en raison duquel les réécritures d’URL ne sont pas générées pour "Toutes les consultations de magasin" pour les produits créés via l’API. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 0898c5b3-d361-4bcb-af3a-7f76ac8a23e1
feature: REST, Categories, Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-35064 : les réécritures d’URL ne sont pas générées pour les variables créées via l’API

Le correctif MDVA-35064 corrige le problème en raison duquel les réécritures d’URL ne sont pas générées pour &quot;Toutes les consultations de magasin&quot; pour les produits créés via l’API. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.17 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.3-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque des produits configurables sont créés via l’API, les réécritures d’URL ne sont pas générées.

<u>Étapes à reproduire</u>:

1. Créez un site web, un magasin et une vue de magasin.
1. Créez une nouvelle catégorie.
1. Créez un produit et affectez-le à la catégorie nouvellement créée.
1. Affectez le produit au site web principal et au nouveau site web.
1. Vérifiez le tableau URL et assurez-vous qu’il contient des entrées pour le produit, la catégorie/le produit pour chaque magasin de chaque site web.
1. Supprimez le produit du deuxième site web.

<u>Résultats attendus</u>:

Le tableau URL contient des entrées pour produit, catégorie/produit uniquement pour les magasins du premier site web.

<u>Résultats réels</u>:

Le tableau URL contient des réécritures d’URL pour tous les magasins de tous les sites web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
