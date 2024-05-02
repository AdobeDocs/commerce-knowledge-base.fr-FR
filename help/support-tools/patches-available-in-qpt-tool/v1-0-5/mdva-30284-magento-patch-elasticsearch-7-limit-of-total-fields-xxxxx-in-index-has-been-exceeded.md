---
title: '''MDVA-30284 Patch : Elasticsearch 7 - La limite du total des champs [XXXXX] dans l''index a été dépassée'''
description: Le correctif MDVA-30284 résout le problème en raison duquel vous recevez un message d’erreur indiquant que "La limite du nombre total de champs \[XXXXX\] dans l’index a été dépassée" lors de l’utilisation d’Elasticsearch 7. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 est installé. L’ID de correctif est MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-30284 Correctif : Elasticsearch 7 - Limite du total des champs [XXXXX] dans l’index a été dépassé

Le correctif MDVA-30284 résout le problème en raison duquel vous recevez un message d’erreur indiquant que &quot;La limite du nombre total de champs \[XXXXX\] dans l’index a été dépassée&quot; lors de l’utilisation d’Elasticsearch 7. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 est installé. L’ID de correctif est MDVA-30284.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.5-p2.
* Elasticsearch 7 est compatible avec Adobe Commerce 2.3.5 et 2.4.x

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La limite des champs Elasticsearch est incorrecte, ce qui entraîne l’erreur suivante lors de l’exécution de l’indexeur \[catalogsearch\_fulltext\] :

*Limite du nombre total de champs [xxx] dans l’index [xxxxxx] a été dépassé*

Ce problème se produit lorsque vous disposez d’un grand nombre d’attributs de produit. Le problème est déclenché par la manière dont Elasticsearch calcule le nombre de champs. Parfois, lorsqu’il y a des attributs auxquels des champs sont affectés, ces champs sont indexés en tant qu’indexeurs distincts. La limite ayant été dépassée, l’avertissement s’affiche.

<u>Étapes à reproduire :</u>

<u>Conditions préalables</u>

* Module-élasticsearch installé 100.3.5.
* Elasticsearch 7 installé.
* Configurez Elasticsearch comme serveur principal de recherche.

1. Créez plus de 1 000 attributs pour les produits.
1. Créez des produits pour chaque famille.
1. Exécutez l’indexeur.

<u>Résultat attendu :</u>

Tous les produits sont disponibles dans l’index Elasticsearch.

<u>Résultat réel :</u>

1. Erreur de l’Elasticsearch :

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Le nouveau produit n’a pas été indexé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
