---
title: "MDVA-36138 : règle de livraison gratuite non appliquée pour plusieurs articles de panier"
description: Le correctif MDVA-36138 corrige le problème en raison duquel, lorsqu’il y a plusieurs articles dans le panier, la SKU correspondante dans la fonction d’expédition gratuite n’est pas appliquée à la livraison gratuite. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 est installé. L’ID de correctif est MDVA-36138. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138 : la règle d’expédition gratuite n’est pas appliquée au panier pour plusieurs articles

Le correctif MDVA-36138 corrige le problème en raison duquel, lorsqu’il y a plusieurs articles dans le panier, la SKU correspondante dans la fonction d’expédition gratuite n’est pas appliquée à la livraison gratuite. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.21 est installée. L’ID de correctif est MDVA-36138. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) version 2.3.2 et ultérieure

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Si une règle de livraison gratuite est appliquée uniquement à des articles spécifiques, la remise ne s’applique pas lorsque d’autres articles sont présents dans le panier.

<u>Étapes à reproduire</u>:

1. Créez des produits simples : simple1 et simple2.
1. Configurez USPS (ou toute méthode de livraison en ligne) :

   * Méthodes autorisées : Priorité du courrier (une méthode sélectionnée dans le but de ne pas avoir une longue liste de méthodes dans le panier et le passage en caisse).
   * Méthode gratuite : Priority Mail.

1. Créez une règle de panier :

   * Définition du code de bon
   * Onglet Conditions : laissez vide
   * Onglet Actions :

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Ajoutez simple1 au panier.
1. Appliquez le code du coupon.
1. Ajoutez simple2 au panier.

<u>Résultats attendus</u>:

* simple1 - doit disposer d’une livraison gratuite.
* simple2 - l’expédition doit être payée.

<u>Résultats réels</u>:

Le prix d’expédition inclut simple1 et simple2.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
