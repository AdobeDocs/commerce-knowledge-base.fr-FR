---
title: "MDVA-29446 : méthode d’expédition non pertinente disponible pour le passage en caisse"
description: Le correctif MDVA-29446 résout le problème lorsqu’une méthode d’expédition non applicable apparaît sur les options de méthode d’expédition de passage en caisse et, si cette option est sélectionnée, un message d’erreur "Opérateur avec une telle méthode non trouvé nul, taux forfaitaire*". s’affiche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Le problème devrait être corrigé dans les versions ultérieures d’Adobe Commerce.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446 : méthode d’expédition non pertinente disponible pour le passage en caisse

Le correctif MDVA-29446 résout le problème lorsqu’une méthode d’expédition non applicable apparaît sur les options de méthode d’expédition de passage en caisse et, si cette option est sélectionnée, un message d’erreur &quot;*Opérateur avec une telle méthode non trouvée nulle, taux forfaitaire*&quot;. s’affiche. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Le problème devrait être corrigé dans les versions ultérieures d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-2.4.0.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problèmes

Vous disposez d’une méthode d’expédition qui n’est pas applicable, mais qui apparaît toujours dans les options de méthode d’expédition de passage en caisse. Vous pouvez sélectionner cette méthode d’expédition non pertinente.

<u>Étapes à reproduire</u> :

1. Installez clean 2.3-development.
1. Activez le taux plat et définissez :

   * Ship to Applicable Countries = *Specific Countries*
   * Ship to Specific Countries = *Antarctica*
   * Afficher la méthode si non applicable = *Oui*

1. Désactivez tous les autres modes de livraison.
1. Positionnez-vous au niveau du front-end, et créez un client avec une adresse américaine.
1. Sélectionnez un élément et cliquez sur **Ajouter au panier**.
1. Cliquez sur le panier et cliquez sur **Passez en caisse**.

<u>Résultats réels</u> :

1. Sur la page **Expédition**, vous voyez ce qui suit :

   * Le taux plat est visible
   * Taux d&#39;aplatissement : 0 $
1. Une fois que l’utilisateur a cliqué sur **Suivant**, l’utilisateur obtient l’erreur suivante :

*&quot;Opérateur avec une telle méthode introuvable : null, flatrate&quot;*

<u>Résultats attendus</u> :

* Le prix du mode de livraison n’est pas visible si le mode de livraison n’est pas applicable.
* Le bouton **Suivant** ne doit pas être actif.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
