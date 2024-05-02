---
title: 'MDVA-40101 : les articles restent mini-panier après le placement de la commande PayPal Express Checkout'
description: Le correctif MDVA-40101 corrige le problème en raison duquel les articles ne sont pas supprimés du mini-panier après un placement de commande réussi à l’aide de PayPal Express Checkout. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 est installé. L’ID de correctif est MDVA-40101. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.0.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101 : Les articles restent mini-panier après le placement de la commande PayPal Express Checkout

Le correctif MDVA-40101 corrige le problème en raison duquel les articles ne sont pas supprimés du mini-panier après un placement de commande réussi à l’aide de PayPal Express Checkout. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.1.4 est installée. L’ID de correctif est MDVA-40101. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les articles restent dans le mini-panier même après un placement de commande réussi à l’aide de PayPal Express Checkout.

<u>Étapes à reproduire</u>:

passez une commande en utilisant le paiement express PayPal en mode Incognito dans un navigateur.

<u>Résultats attendus</u>:

Le mini-panier doit être vide une fois la commande passée.

<u>Résultats réels</u>:

* La page de succès affiche un mini-panier vide.
* Toutes les autres pages affichent un mini-panier avec les articles achetés.
* Cliquer sur le lien du panier vous redirige vers une page de panier vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
