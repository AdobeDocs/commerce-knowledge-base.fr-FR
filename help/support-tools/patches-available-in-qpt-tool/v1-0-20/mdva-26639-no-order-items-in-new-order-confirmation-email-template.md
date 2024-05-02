---
title: '''MDVA-26639 : aucun élément de commande dans le nouveau modèle d''email de confirmation de commande'''
description: Le correctif MDVA-26639 corrige le problème lors de la création d’une commande. Les éléments de commande sont manquants dans un modèle d’email de confirmation.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639 : aucun élément de commande dans le nouveau modèle d’email de confirmation de commande

Le correctif MDVA-26639 corrige le problème lors de la création d’une commande. Les éléments de commande sont manquants dans un modèle d’email de confirmation.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.20 est installée. L’ID de correctif est MDVA-26639. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.3-p1

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Accédez à **Magasins** > **Configuration** > **Ventes** > **Courriers électroniques de vente** > **Nouvelle confirmation de commande** et sélectionnez **Modèle : nouvel ordre de sélection**.
1. Accédez à **Ventes** > **Ordre : sélectionnez une commande.**, puis accédez à **Informations**, puis sélectionnez **Envoyer un courrier**.

<u>Résultats attendus</u>:

Les éléments de commande s’affichent dans le courrier électronique de commande du client, comme prévu.

<u>Résultats réels</u>:

Les éléments de commande sont manquants dans l’email de commande du client. Il en va de même si vous créez un modèle et sélectionnez un modèle New Order ou New Order (Luma).

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
