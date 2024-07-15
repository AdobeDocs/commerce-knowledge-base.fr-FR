---
title: "Correctif MDVA-33704 : la récupération en magasin ne s’affiche pas"
description: Le correctif MDVA-33704 résout le problème en raison duquel les produits avec l’option de récupération en magasin ne s’affichent pas comme méthode d’expédition.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Correctif MDVA-33704 : la récupération en magasin ne s’affiche pas

Le correctif MDVA-33704 résout le problème en raison duquel les produits avec l’option de récupération en magasin ne s’affichent pas comme méthode d’expédition.

Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-33704. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.0-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Condition préalable requise</u>:<br>

**Pick in Store** activé

<u>Étapes à reproduire</u> :

1. Ajoutez un produit au panier.
1. Accédez à Passage en caisse.
1. Ajoutez des informations d’expédition et choisissez n’importe quel mode d’expédition autre que la récupération en magasin.
1. Sélectionnez **Passez au paiement**, mais ne passez pas à la page de paiement.
1. Revenez plutôt à la section **Contact et expédition** .
1. Sélectionnez **Pickup**.
1. Sélectionnez **Magasin** et **Clic sur paiement**.
1. Notez que votre adresse de livraison est automatiquement renseignée comme adresse de facturation.
1. Actualisez la page web.

<u>Résultats attendus</u> :

L’option de récupération en magasin s’affiche comme méthode d’expédition, comme prévu.

<u>Résultats réels</u> :

L’option de récupération en magasin ne s’affiche pas comme méthode d’expédition.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
