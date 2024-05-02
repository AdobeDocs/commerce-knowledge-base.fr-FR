---
title: 'MDVA-37068 : taxe incorrecte affichée sur le passage en caisse pour les produits virtuels'
description: Le correctif MDVA-37068 corrige le problème lorsque la page Passage en caisse affiche un taux d’imposition incorrect pour les produits virtuels. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 est installé. L’ID de correctif est MDVA-37068. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068 : taxe incorrecte affichée sur le passage en caisse pour les produits virtuels

Le correctif MDVA-37068 corrige le problème lorsque la page Passage en caisse affiche un taux d’imposition incorrect pour les produits virtuels. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.26 est installée. L’ID de correctif est MDVA-37068. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce (toutes les méthodes de déploiement) 2.3.1-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de taxe incorrect s’affiche sur la page Passage en caisse lorsque le panier ne contient que des produits virtuels.

<u>Conditions préalables</u>:

1. Créer deux taux d&#39;imposition et règles fiscaux distincts pour deux pays différents - par exemple 10 % et 1 %.
1. Créez un produit virtuel.
1. Exécutez la réindexation et videz le cache.

<u>Étapes à reproduire</u>:

1. Créez un client.
1. Ajoutez différentes adresses de facturation et de livraison.
1. Ajoutez un produit virtuel au panier.
1. Consultez la page Panier et passage en caisse .

<u>Résultats attendus</u>:

La taxe affichée sur la page Panier et passage en caisse est la même.

<u>Résultats réels</u>:

La taxe affichée sur la page Panier et passage en caisse n’est PAS la même.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
