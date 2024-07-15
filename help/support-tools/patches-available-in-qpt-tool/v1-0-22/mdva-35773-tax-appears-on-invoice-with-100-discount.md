---
title: "MDVA-35773 : La taxe apparaît sur une facture avec une remise de 100 %"
description: Le correctif MDVA-35773 corrige le problème en raison duquel le total général n’apparaissait pas comme zéro sur la facture pour les commandes avec une remise de 100 %. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-35773. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773 : La taxe apparaît sur une facture avec une remise de 100 %

Le correctif MDVA-35773 corrige le problème en raison duquel le total général n’apparaissait pas comme zéro sur la facture pour les commandes avec une remise de 100 %. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 est installé. L’ID de correctif est MDVA-35773. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.6

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.6-2.3.7 et 2.4.1-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > **Paramètres** > **Configuration** > **Ventes** > **Taxe**.
1. Définissez **Prix du catalogue** et **Appliquer une réduction sur les prix** sur *Impôt compris*.
1. Accédez à **Magasins** > **Règles fiscales** > **Ajouter une nouvelle règle fiscale**.
1. Créez une règle fiscale (par exemple : tous les Etats-Unis avec un taux d&#39;imposition de 10%) et appliquez-la.
1. Accédez à **Marketing** > **Règles de prix du panier** et **Ajouter une nouvelle règle**.
1. Créez une règle avec une **remise de 100 % pour tous les utilisateurs**.
1. Effectuez une commande sur le storefront :

   * Sélectionnez **Livraison gratuite**.
   * Appliquez le **Code coupon**.

1. Accédez à **Sales** > **Commandes** et ouvrez votre commande.
1. Créez une facture pour la commande et ouvrez-la.

<u>Résultats attendus</u> :

Total général de la facture = *$0.0*.

<u>Résultats réels</u> :

La facture Total général = *montant de la taxe* est créée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
