---
title: 'MDVA-40175 : Boutons radio non affichés lors de la réorganisation'
description: Le correctif MDVA-40175 résout le problème en raison duquel les boutons radio ne s’affichent pas lorsque les utilisateurs tentent de les réorganiser. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-40175. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175 : Boutons radio non affichés lors d’une réorganisation

Le correctif MDVA-40175 résout le problème en raison duquel les boutons radio ne s’affichent pas lorsque les utilisateurs tentent de les réorganiser. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.10 est installée. L’ID de correctif est MDVA-40175. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les boutons radio ne s’affichent pas dans la section Informations de paiement et d’expédition lorsque les utilisateurs tentent de procéder à une nouvelle commande.

<u>Conditions préalables</u>:

1. Un compte client avec une adresse de livraison et une adresse de facturation est créé.
1. Un produit simple est créé.
1. Plusieurs méthodes de diffusion sont configurées.
1. Au moins une commande est créée.

<u>Étapes à reproduire</u>:

1. Accédez au panneau Admin > **Ventes** > **Commandes**.
1. Sélectionnez l’ordre créé.
1. Cliquez sur le bouton **Affichage** lien.
1. Cliquez sur le bouton **Réorganiser** bouton .
1. Faites défiler la page vers le bas jusqu’à la fonction **Informations de paiement et d’expédition** .
1. Cliquez sur le bouton **Cliquez pour modifier le mode de livraison.**.

<u>Résultats attendus</u>:

La liste des méthodes de diffusion avec boutons radio s&#39;affiche.

<u>Résultats réels</u>:

La liste des méthodes de diffusion sans bouton radio s&#39;affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
