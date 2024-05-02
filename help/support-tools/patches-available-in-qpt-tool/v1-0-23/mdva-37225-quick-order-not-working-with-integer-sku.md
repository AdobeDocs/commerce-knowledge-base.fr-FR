---
title: 'MDVA-37225 : l’ordre rapide ne fonctionne pas avec le SKU entier'
description: Le correctif de qualité MDVA-37225 pour Adobe Commerce corrige le problème lorsque la page ne se charge pas lors de la création d’un ordre rapide lorsqu’il existe une valeur entière dans les SKU importés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 est installé. L’ID de correctif est MDVA-37225. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225 : l’ordre rapide ne fonctionne pas avec un SKU entier.

Le correctif de qualité MDVA-37225 pour Adobe Commerce corrige le problème lorsque la page ne se charge pas lors de la création d’un ordre rapide lorsqu’il existe une valeur entière dans les SKU importés. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.23 est installée. L’ID de correctif est MDVA-37225. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.4.1-p1
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.1-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Condition requise</u>:

Adobe Commerce avec module B2B installé

<u>Étapes à reproduire</u>:

1. Activez la fonctionnalité d’ordre rapide B2B.
1. Créez 4 produits simples avec des SKU (exemples de SKU) : *00100*, *001E002*, *001E02C*, et *7100824*).
1. Accédez au ``<storefront_url>/quickorder`` sur le front-end, et essayez de créer une commande à l’aide d’un fichier CSV avec ce contenu d’ exemple :

| sku | qty |
|---|---|
| 00100 | 1 |


<u>Résultats attendus</u>:

Le produit (exemple : produit avec SKU = *00100*) est ajouté au panier, comme prévu.

<u>Résultats réels</u>:

La page ne se charge pas et aucun produit n’est ajouté au panier.


## Appliquer le correctif

Pour appliquer des correctifs individuels, suivez les liens suivants dans la documentation destinée aux développeurs, en fonction de votre produit Adobe Commerce :

* Adobe Commerce et Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de qualité dans notre base de connaissances de support, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de notre base de connaissances en matière de soutien.
