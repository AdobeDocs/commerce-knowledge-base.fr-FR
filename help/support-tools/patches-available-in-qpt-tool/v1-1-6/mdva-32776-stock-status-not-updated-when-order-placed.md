---
title: 'MDVA-32776 : statut des stocks non mis à jour avec emplacement de commande'
description: Le correctif MDVA-32776 corrige le problème où l’état du stock n’est pas mis à jour lorsqu’une commande est passée mais n’est pas expédiée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 est installé. L’ID de correctif est MDVA-32776. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776 : statut des stocks non mis à jour avec emplacement de commande

Le correctif MDVA-32776 corrige le problème où l’état du stock n’est pas mis à jour lorsqu’une commande est passée mais n’est pas expédiée. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 est installé. L’ID de correctif est MDVA-32776. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut du stock n&#39;est pas mis à jour lorsqu&#39;une commande est passée mais qu&#39;elle n&#39;est pas expédiée.

<u>Conditions préalables</u> :

1. Le module Inventaire est installé.
1. L’affichage des produits en rupture de stock est défini sur *Oui*.

   Pour définir, accédez à **Magasins** > **Configuration** > **Catalogue** > **Inventaire** > **Afficher les produits en rupture de stock** = *Oui*.

<u>Étapes à reproduire</u> :

1. Créez deux produits simples avec qty = 11 et 22.
1. Créez un produit groupé à l’aide des produits simples créés à l’étape 1.
1. Ajoutez des produits regroupés au panier en définissant la quantité d’un produit sur 11 et en mettant l’autre produit simple en rupture de stock.
1. Effectuez le passage en caisse et passez la commande.

<u>Résultats attendus</u> :

Les produits regroupés affichent `out-of-stock` étiquettes lorsque les produits simples associés sont en rupture de stock.

<u>Résultats réels</u> :

1. Le produit simple avec quantité = 11 est en rupture de stock.
1. Le produit groupé n’affiche pas de message *d’usine* pour le produit avec une quantité = 11. Cependant, l’ajout de ce produit au panier génère une erreur *out-of-stock*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
