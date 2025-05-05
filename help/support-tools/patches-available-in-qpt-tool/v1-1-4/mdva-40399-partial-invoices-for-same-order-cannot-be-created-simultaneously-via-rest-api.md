---
title: "MDVA-40399 : les factures partielles pour une même commande ne peuvent pas être créées simultanément via l’API"
description: Le correctif MDVA-40399 corrige le problème en raison duquel les factures partielles pour la même commande ne peuvent pas être créées simultanément via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 est installé. L’ID de correctif est MDVA-40399. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399 : Les factures partielles pour une même commande ne peuvent pas être créées simultanément via l’API

Le correctif MDVA-40399 corrige le problème en raison duquel les factures partielles pour la même commande ne peuvent pas être créées simultanément via l’API REST. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 est installé. L’ID de correctif est MDVA-40399. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les factures partielles pour les mêmes commandes ne peuvent pas être créées simultanément à l’aide de l’API REST.

<u>Conditions préalables</u> :

Un produit configurable avec au moins deux variantes.

<u>Étapes à reproduire</u> :

1. Ajoutez les deux variantes du produit configurable au panier.
1. Placez la commande.
1. Créez deux factures simultanément pour la commande via l’API REST.

<u>Résultats attendus</u> :

* Les deux factures doivent être créées avec succès.
* `qty_invoiced` doit être mis à jour pour les deux factures dans la table `sales_order_item`.
* Les deux produits doivent avoir une quantité facturée.

<u>Résultats réels</u> :

* Les deux factures ont été créées avec succès.
* `qty_invoiced` n’est pas mis à jour par rapport à l’une des factures de la table `sales_order_item`.
* Sur la page **Vue de la commande** de l’administrateur, la quantité de factures s’affiche uniquement pour un produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
