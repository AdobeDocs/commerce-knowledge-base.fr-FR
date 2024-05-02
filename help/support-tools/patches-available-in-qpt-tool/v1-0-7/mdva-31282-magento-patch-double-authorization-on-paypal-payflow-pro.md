---
title: 'MDVA-31282 : double autorisation sur Paypal PayFlow Pro'
description: Le correctif MDVA-31282 résout le problème lorsque deux autorisations se produisent sur Paypal PayFlow Pro dans Adobe Commerce. Les doubles autorisations ont également pour effet de contourner les filtres de fraude de PayFlow Pro et de doubler les frais de transaction. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282 : double autorisation sur Paypal PayFlow Pro

Le correctif MDVA-31282 résout le problème lorsque deux autorisations se produisent sur Paypal PayFlow Pro dans Adobe Commerce. Les doubles autorisations ont également pour effet de contourner les filtres de fraude de PayFlow Pro et de doubler les frais de transaction. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.7 est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.3.3 et 2.3.5 - 2.3.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les doubles autorisations se produisent dans PayPal PayFlow Pro dans Adobe Commerce, ce qui a pour effet de contourner les filtres de fraude de PayFlow Pro et de doubler les frais de transaction.

<u>Conditions préalables</u>:

Configurez le mode de paiement PayPal PayFlow Pro.

<u>Étapes à reproduire</u>:

1. Positionnez-vous sur le front-end en tant que client invité.
1. Ajouter des produits à **Panier** à partir des pages de produits.
1. Passez à **Passage en caisse**.
1. Spécifier **Adresse de livraison** comme adresse dans Country \#1 (Exemple : adresse du Royaume-Uni), et sélectionnez un mode de livraison.
1. Sélectionner **PayPal PayFlow Pro** comme mode de paiement. Spécifiez la variable **Adresse de facturation** comme adresse dans Country \#2 (Exemple : adresse des Etats-Unis).
1. Saisissez les données de la carte de crédit et passez la commande.
1. Accédez à **Ventes** > **Commandes** dans admin et observez l’ordre créé.

<u>Résultats attendus</u>:

* Le bloc Informations de paiement s’affiche : *&quot;Triggers Fraud Filters : RESPMSG : En cours de révision par Fraud Service*. *La commande est à l’état Fraude présumée&quot;*.
* Paypal PayFlow Pro affiche une seule transaction d’autorisation, comme prévu.

<u>Résultats réels</u>:

* Le bloc Informations de paiement s’affiche : *&quot;Triggers Fraud Filters : RESPMSG : En cours de révision par Fraud Service*. *La commande est en état de traitement&quot;*.
* Paypal PayFlow Pro affiche les transactions de double autorisation.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
