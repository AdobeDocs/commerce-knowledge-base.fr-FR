---
title: "MDVA-33992 : tarification personnalisée B2B pour le grossiste non affiché dans le panier"
description: Le correctif MDVA-33992 corrige le problème en raison duquel la tarification personnalisée pour un client B2B n’est pas prise en compte lorsqu’un produit est ajouté à un panier. Ce correctif est disponible lorsque l’outil de correctifs de qualité (QPT) 1.0.15 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992 : Prix personnalisé B2B pour le grossiste non affiché dans le panier

Le correctif MDVA-33992 corrige le problème en raison duquel la tarification personnalisée pour un client B2B n’est pas prise en compte lorsqu’un produit est ajouté à un panier. Ce correctif est disponible lorsque l’outil de correctifs de qualité (QPT) 1.0.15 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.1 avec B2B

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0-2.4.1-p1 avec B2B

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La tarification personnalisée pour un client B2B n’est pas prise en compte lorsqu’un produit est ajouté à un panier.

<u>Étapes à reproduire</u> :

Le problème est reproductible pour la version B2B avec le catalogue partagé activé.

1. Créez une entreprise B2B avec un catalogue partagé personnalisé affecté.
1. Créez un produit dans le catalogue personnalisé de l’entreprise avec un prix personnalisé (prix de niveau).
1. En tant que client B2B, vérifiez que le prix personnalisé du produit s’affiche dans le catalogue.
1. En tant que client B2B, ajoutez le produit au panier.

<u>Résultat attendu</u> :

Le prix correct est affiché dans le panier et correspond au prix dans le catalogue.

<u>Résultat réel</u> :

Le prix personnalisé disparaît et le prix normal du catalogue par défaut s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
