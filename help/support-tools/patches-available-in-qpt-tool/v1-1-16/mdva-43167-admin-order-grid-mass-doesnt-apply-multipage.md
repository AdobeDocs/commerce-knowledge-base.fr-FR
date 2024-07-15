---
title: "MDVA-43167 : L’action en masse de la grille d’ordre d’administration ne s’applique pas pour les pages multiples"
description: Le correctif MDVA-43167 corrige le problème en raison duquel l’action de masse de la grille d’ordre d’administration ne s’applique pas pour les pages multiples lorsque l’utilisateur administrateur sélectionne toutes les commandes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-43167. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 58a126db-8a4f-4e20-8fe5-3ce2e25edf7e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-43167 : L’action en masse de la grille d’ordre d’administration ne s’applique pas pour les pages multiples.

Le correctif MDVA-43167 corrige le problème en raison duquel l’action de masse de la grille d’ordre d’administration ne s’applique pas pour les pages multiples lorsque l’utilisateur administrateur sélectionne toutes les commandes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-43167. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’action en masse de la grille d’ordre d’administration ne s’applique pas pour les pages multiples lorsque l’utilisateur administrateur sélectionne toutes les commandes.

<u>Étapes à reproduire</u> :

1. Achetez n’importe quel produit trois fois pour créer trois commandes.
1. Accédez à la **grille des commandes commerciales**.
1. Remplacez la pagination par une valeur personnalisée de 2.
1. Sélectionnez tout.
1. Sélectionnez **Suspendre une action en masse**.

<u>Résultats attendus</u> :

Les trois commandes sont suspendues.

<u>Résultats réels</u> :

Seules les deux commandes visibles sont suspendues.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
