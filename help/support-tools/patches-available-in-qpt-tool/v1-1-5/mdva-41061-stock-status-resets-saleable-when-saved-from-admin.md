---
title: "MDVA-41061 : le statut des stocks est réinitialisé à la vente lorsque le produit est enregistré depuis l’administrateur"
description: Le correctif MDVA-41061 corrige le problème en raison duquel l’état du stock est réinitialisé sur vendable lorsque le produit est enregistré depuis l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 est installé. L’ID de correctif est MDVA-41061. La dernière version de correctif est disponible dans QPT 1.1.15 avec l’ID de correctif MDVA-41061-V3. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061 : Le statut des stocks est réinitialisé à la vente lorsque le produit est enregistré depuis l’administrateur.

Le correctif MDVA-41061 corrige le problème en raison duquel l’état du stock est réinitialisé sur vendable lorsque le produit est enregistré depuis l’administrateur. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 est installé. L’ID de correctif est MDVA-41061. La dernière version de correctif est disponible dans QPT 1.1.15 avec l’ID de correctif MDVA-41061-V3. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut des stocks est réinitialisé à la vente lorsque le produit est enregistré depuis l’administrateur.

<u>Conditions préalables</u> :

Les modules d’inventaire sont installés.

<u>Étapes à reproduire</u> :

1. Créez un produit simple avec Qté = 1.
1. passé une commande à l’aide du produit créé à l’étape 1 ;
1. Exécutez cron : assurez-vous que la file d’attente `inventory.reservations.updateSalabilityStatus` est exécutée et que l’état du stock de produit a été remplacé par zéro dans la table `cataloginventory_stock_status`.
1. Vérifiez le produit sur le front-end. Elle doit être marquée comme **Out of Stock**.
1. Enregistrez le produit dans l’administrateur sans aucune modification.

<u>Résultats attendus</u> :

* L’état du stock ne doit pas être mis à jour.
* Le produit doit être **Out of Stock** sur le front-end.

<u>Résultats réels</u> :

* Le produit simple est marqué comme **In Stock** sur le front-end.
* Les utilisateurs reçoivent le message *La quantité demandée n&#39;est pas disponible* lorsqu&#39;ils tentent de l&#39;ajouter au panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
