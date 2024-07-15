---
title: 'MDVA-30837 : montant minimum de la commande pour la livraison gratuite'
description: Le correctif MDVA-30837 ajoute des options de configuration pour le calcul de la livraison gratuite afin que l’utilisateur puisse configurer le Montant minimum de la commande pour obtenir la livraison gratuite en fonction du Sous-total (ou Total général). Cela permet des personnalisations locales pour les méthodes de taxe et d’expédition. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837 : montant minimum de la commande pour la livraison gratuite

Le correctif MDVA-30837 ajoute des options de configuration pour le calcul de la livraison gratuite afin que l’utilisateur puisse configurer le Montant minimum de la commande pour obtenir la livraison gratuite en fonction du Sous-total (ou Total général). Cela permet des personnalisations locales pour les méthodes de taxe et d’expédition. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif MDVA-30837 ajoute le paramètre de configuration pour configurer le paramètre **Montant minimum de la commande** afin d’obtenir la livraison gratuite en fonction du Sous-total (ou Total général) :

* **Inclure la taxe au montant** : *Oui/Non* dans la configuration de la méthode d’expédition gratuite.
   * Lorsque **Inclure la taxe au montant** est défini sur *Oui*, le montant minimum de la commande est calculé comme suit : Sous-total + Taxe - Remise.
   * Lorsque **Inclure la taxe au montant** est défini sur *Non*, le montant minimum de la commande est calculé comme Sous-total - Remise.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > Paramètres > **Configuration** > **Ventes** > **Taxe** et définissez les éléments suivants :

   * Calcul des taxes basé sur *l’adresse de livraison*
   * Activer le commerce transfrontalier : *Non*
   * Afficher les prix des produits dans le catalogue : *Taxe d’exclusion*
   * Afficher les prix de livraison : *Exclusion de taxe*
   * Prix d’affichage : *Taxe d’exclusion*
   * Afficher le sous-total : *Exclure la taxe*
   * Afficher le montant de livraison : *Exclure la taxe*
   * Afficher les prix d’emballage cadeau : *Exclusion de taxe*
   * Afficher les prix des cartes imprimées : *Exclure la taxe*
   * Inclure la taxe dans le total de la commande : *Oui*
   * Afficher le résumé complet des taxes : *Oui*

1. Accédez à **Sales** > **Shipping Settings** > **Free Shipping** et définissez **Minimum Order Amount** = *30*.
1. Accédez à **Marketing** > Promotions > **Règles de prix du panier** et créez une règle de prix (pour obtenir des instructions détaillées, reportez-vous à la section [Créer une règle de prix du panier](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) dans notre guide d’utilisation).

   * Code coupon = *coupon spécifique*.
   * Conditions : le sous-total est égal ou supérieur à 25 $.
   * Actions : Expédition gratuite = *Pour les envois dont les articles correspondent*.

1. Créez un produit au prix de 23,10 $.
1. Ajoutez la taxe CA à la règle de taxe par défaut.
1. Ajoutez ce produit au panier.
1. Obtenez un devis de livraison - après taxes, le total général = 25,01 $ et la livraison gratuite est appliquée.
1. Appliquez le code de coupon : il ne sera pas valide, car le sous-total (taxe d’exclusion) est de 23,10 $.

<u>Résultats attendus</u> :

Il existe un autre paramètre de configuration - Inclure la taxe sur le montant : *Oui*/*Non* dans la configuration de la méthode de livraison gratuite :

* Lorsque l’option Inclure la taxe sur le montant est définie sur *Oui*, le Montant minimum de la commande est calculé comme suit : Sous-total + Taxe - Remise.
* Lorsque l’option Inclure la taxe sur le montant est définie sur *Non*, le Montant minimum de la commande est calculé comme Sous-total - Remise.

<u>Résultats réels</u> :

La condition de la règle de prix d’expédition libre ne peut être basée que sur le sous-total, tandis que la méthode d’expédition gratuite ne peut être basée que sur le total général.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
