---
title: "MDVA-36021 : les utilisateurs reçoivent un message d’erreur lors de l’ouverture des détails de la commande"
description: Le correctif MDVA-36021 résout le problème où les utilisateurs reçoivent le message d’erreur *Call to a member function getId()* lors de la tentative d’ouverture des détails de la commande. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 est installé. L’ID de correctif est MDVA-36021. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021 : les utilisateurs reçoivent un message d’erreur lors de l’ouverture des détails de la commande

Le correctif MDVA-36021 résout le problème où les utilisateurs obtiennent des *Appel à une fonction membre getId()* message d’erreur lors de la tentative d’ouverture des détails de la commande. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.1 est installée. L’ID de correctif est MDVA-36021. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.4.1, 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque les utilisateurs tentent d’ouvrir les détails de la commande, le message d’erreur suivant s’affiche sur la page des détails de la commande dans l’Admin : *report.CRITICAL : Erreur : appel à une fonction membre getId() sur le tableau dans /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

<u>Conditions préalables</u>:

Le système doit avoir des paramètres fiscaux et des commandes avec des taux d&#39;imposition spécifiques.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Ventes** > **Commandes** > **Ouvrir la commande**.

<u>Résultats attendus</u>:

La commande est ouverte sans erreur.

<u>Résultats réels</u>:

Vous obtenez un message d’erreur similaire à ce qui suit : *report.CRITICAL : Erreur : appel à une fonction membre getId() sur le tableau dans /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
