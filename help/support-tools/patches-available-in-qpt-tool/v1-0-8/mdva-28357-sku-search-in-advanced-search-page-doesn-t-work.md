---
title: La recherche de SKU MDVA-28357 dans la page Recherche avancée ne fonctionne pas.
description: Le MDVA-28357 résout le problème en raison duquel la recherche par SKU d’un produit dans la page Recherche avancée n’entraîne pas l’affichage du produit concerné dans les résultats de recherche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.1.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# La recherche de SKU MDVA-28357 dans la page Recherche avancée ne fonctionne pas.

Le MDVA-28357 résout le problème en raison duquel la recherche par SKU d’un produit dans la page Recherche avancée n’entraîne pas l’affichage du produit concerné dans les résultats de recherche. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.1.

## Produits et versions concernés

* Ce correctif a été conçu pour Adobe Commerce sur site 2.3.4-p2.
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0 à 2.3.5-p2 et 2.4.0 à 2.4.0-p1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Dans une recherche avancée, la recherche à l’aide d’un SKU interroge le champ SKU à l’aide d’un caractère générique. Mais un caractère générique ne peut être utilisé qu’avec `sku.keyword`, donc cela ne renvoie pas le produit attendu.

<u>Étapes à reproduire</u>

1. Accédez à la page Recherche avancée .
1. Recherchez par numéro de SKU.

<u>Résultat réel</u>

Le message d’erreur s’affiche : *Nous ne trouvons aucun élément correspondant à ces critères de recherche. Modifier votre recherche*.

<u>Résultat attendu</u>

Un produit s’affiche avec un message : *1 élément a été trouvé en utilisant les critères de recherche suivants :*  *SKU : XX-XXXX*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Application de correctifs à l’aide de l’outil Correctifs de qualité](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
