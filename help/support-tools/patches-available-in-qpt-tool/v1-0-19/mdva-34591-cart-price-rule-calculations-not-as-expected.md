---
title: 'MDVA-34591 : calculs des règles de prix du panier non comme prévu'
description: Le correctif MDVA-34591 corrige le problème en raison duquel la règle de prix du panier avec **Remise maximale sur la qualité est appliquée à** ne fonctionne pas correctement si plusieurs règles de prix de panier sont appliquées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-34591. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591 : calculs des règles de prix du panier non comme prévu

Le correctif MDVA-34591 corrige le problème en raison duquel la règle de prix du panier avec **Maximum Qty Discount is Applied To** ne fonctionne pas correctement si plusieurs règles de prix de panier sont appliquées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-34591. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.6

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur et créez les deux règles suivantes :

   * Règle 1 : 10 $ sur un maximum de trois articles dans le panier. Définissez la priorité = *3*.
   * Règle 2 : 50 % de réduction sur tous les produits du panier. Définissez la priorité = *1*.

1. Allez à la vitrine.

1. Ajoutez huit quantités d’un produit au prix = *$51* chacune dans le panier.

1. Vérifiez le montant de la remise dans le panier.

<u>Résultats attendus</u> :

La remise calculée correcte est de 234 $, comme prévu.

* Calculs :

  Règles de prix du panier correspondantes : Règle 2, Règle 1\
  Appliquez la règle 2 (remise de 50 %), afin que Discount = 204 $\
  Appliquez la règle 1 (10 articles sur 3), afin que Discount = 30 $\
  Remise totale = MIN ( 408/2 + 10x3, 8 &#42; 51) = MIN (204 + 30, 8 &#42; 51) = 234 $

<u>Résultats réels</u> :

La remise est incorrectement calculée à 153 $, en raison de la mauvaise quantité utilisée pour calculer la valeur de remise maximale, car le montant de remise fixe est appliqué quel que soit le montant des produits dans le panier.

* Calculs :

  Règles de prix du panier correspondantes : Règle 2, Règle 1\
  Appliquez la règle 2 (remise de 50 %), afin que Discount = 204 $\
  Appliquez la règle 1 (10 articles sur 3), afin que Discount = 30 $\
  Réduction totale = MIN (204 + 30, 3 &#42; 51) = 153 $

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
