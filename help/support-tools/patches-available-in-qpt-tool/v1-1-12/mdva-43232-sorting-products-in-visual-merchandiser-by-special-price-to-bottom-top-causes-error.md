---
title: 'MDVA-43232 : Le tri des produits dans le marchandisage visuel par Prix spécial au plus haut (ou au bas) provoque une erreur'
description: Le correctif MDVA-43232 corrige le problème en raison duquel le tri des produits dans le marchandiseur visuel par Prix spécial au haut (ou au bas) provoquait une erreur lors de l’enregistrement de la catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-43232. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232 : Le tri des produits dans le marchandisage visuel par Prix spécial au haut (ou au bas) provoque une erreur.

Le correctif MDVA-43232 corrige le problème en raison duquel le tri des produits dans le marchandiseur visuel par Prix spécial au haut (ou au bas) provoquait une erreur lors de l’enregistrement de la catégorie. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.12 est installée. L’ID de correctif est MDVA-43232. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri des produits dans le marchandiseur visuel par Prix spécial au plus haut (ou au bas) entraîne une erreur lors de l’enregistrement de la catégorie.

<u>Étapes à reproduire</u>:

1. Assurez-vous qu&#39;il y a deux sites web.
1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **Prix** et définissez Périmètre du prix du catalogue = site web.
1. Une fois de plus, accédez à **Magasins** > **Configuration** > **Catalogue** > **Marchandisage visuel** > **Attributs visibles pour les règles de catégorie** > et ajoutez Prix spécial.
1. Créez un produit simple et affectez-lui les deux sites web.
1. Ajoutez un prix spécial à la portée par défaut du produit.
1. Basculez vers la portée de l’autre magasin et remplacez le Prix et le Prix spécial de ce produit.
1. Effectuez une `catalog_product_price` réindexer.
1. Accédez à **Catalogue** > **Catégories** et créez une nouvelle catégorie.
1. Ajoutez une règle de catégorie pour filtrer les produits à prix spécial.
1. Enregistrez la catégorie.
1. Dans la section Produits de la catégorie, définissez Ordre de tri = Prix spécial sur le haut (ou le bas).
1. Enregistrez à nouveau la catégorie.

<u>Résultats attendus</u>:

La catégorie est enregistrée sans erreur.

<u>Résultats réels</u>:

Une exception est générée :

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
