---
title: 'MDVA-41350 : exception lorsque l’administrateur ajoute des produits en dehors de leur accès'
description: Le correctif MDVA-41350 corrige le problème lorsqu’une erreur d’exception est générée au lieu d’une notification d’accès limitée lorsqu’un utilisateur administrateur ajoute un produit dans la commande par SKU qui est hors de son accès. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé. L’ID de correctif est MDVA-41350. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350 : exception lorsque l’administrateur ajoute des produits en dehors de leur accès

Le correctif MDVA-41350 corrige le problème lorsqu’une erreur d’exception est générée au lieu d’une notification d’accès limitée lorsqu’un utilisateur administrateur ajoute un produit dans la commande par SKU qui est hors de son accès. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.11 est installée. L’ID de correctif est MDVA-41350. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un utilisateur administrateur disposant d’un accès restreint ajoute un produit par SKU en dehors de son accès dans l’ordre, une exception se produit au lieu d’un message l’informant de son accès limité.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur en tant qu’utilisateur ayant accès à un site web spécifique uniquement.
1. Accédez à **Ventes** > **Commandes** et cliquez sur **Créer une commande**.
1. Sélectionnez un client et une vue de magasin.
1. Cliquez sur **Ajout de produits par SKU**.
1. Recherchez un SKU qui n’est affecté à aucun site web ou qui n’est pas affecté au site web auquel vous avez accès.
1. Cliquez sur **Ajouter à la commande**.

<u>Résultats attendus</u>:

Un message d’erreur approprié s’affiche.

<u>Résultats réels</u>:

Une exception se produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
