---
title: '''MDVA-44940 : erreur SQL lors de l''enregistrement de la catégorie depuis l''administrateur'''
description: Le correctif MDVA-44940 corrige le problème d’erreur SQL lors de l’enregistrement d’une catégorie depuis l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-44940. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940 : erreur SQL lors de l&#39;enregistrement de la catégorie depuis l&#39;administrateur

Le correctif MDVA-44940 corrige le problème d’erreur SQL lors de l’enregistrement d’une catégorie depuis l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-44940. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur SQL se produit lors de l’enregistrement d’une catégorie à partir de l’administrateur.

<u>Étapes à reproduire</u> :

1. Installez des exemples de données.
1. Créez un deuxième site web avec un groupe de magasins affecté à la catégorie par défaut.

   * Créez une vue de magasin affectée au nouveau groupe de magasins.

1. Créez un stock et une source supplémentaire affectée à ce stock ainsi qu’un canal de vente affecté au second site web.
1. Créez un produit test affecté au deuxième site web.
1. Accédez à **Admin** > **Catalogue** > **Catégories**, sélectionnez **Portée** = **Second site Web** et accédez à **Produits de la catégorie** > **Tri automatique** > Déplacer les produits en rupture de stock vers le bas, puis cliquez sur **Enregistrer**} .

<u>Résultats attendus</u> :

La catégorie est enregistrée.

<u>Résultats réels</u> :

L’erreur suivante se produit : *un problème s’est produit lors de l’enregistrement de la catégorie*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
