---
title: 'MDVA-34189 : le marchandiseur visuel exécute de longues requêtes MySQL'
description: Le correctif MDVA-34189 résout le problème en raison duquel Adobe Commerce exécute de grandes requêtes de marchandisage visuel lors du chargement de la page de catégorie Admin.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189 : le marchandisage visuel exécute de longues requêtes MySQL.

Le correctif MDVA-34189 résout le problème en raison duquel Adobe Commerce exécute de grandes requêtes de marchandisage visuel lors du chargement de la page de catégorie Admin.

Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 est installé. L’ID de correctif est MDVA-34189. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le site Web exécute de grandes requêtes MySQL sur le serveur de production.

<u>Étapes à reproduire</u> :

1. Pour accéder au marchandiseur visuel, accédez à la barre latérale *Admin*, cliquez sur **Catalogue** > **Catégories**.
1. Chargez la page **Catégories** dans le panneau Admin (chargement initial de la catégorie racine) et observez les requêtes qu’elle exécute.

<u>Résultat attendu</u> :

La page Admin **Catégories** doit se charger sans générer de requêtes lentes.

<u>Résultat réel</u> :

Cela dépend de votre configuration PHP. L’exemple le plus courant de cette erreur est que la page **Catégories** ne s’ouvre pas et qu’une erreur *Error 503 first byte timeout* s’affiche.

Par ailleurs, lorsqu’Adobe Commerce charge le marchandisage visuel, il exécute une requête MySQL lente. Cette requête inclut de nombreux ID de produit insérés dans `ORDER BY FIELD(`e`.`entity_id`,  ...)`

dans `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
