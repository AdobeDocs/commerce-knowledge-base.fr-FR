---
title: 'MDVA-34330 : Commandes non filtrées selon le fuseau horaire de l’administrateur'
description: Le correctif MDVA-34330 résout le problème en raison duquel les commandes ne sont pas filtrées selon le fuseau horaire de l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 est installé. L’ID de correctif est MDVA-34330. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: cb369ee3-60b0-4317-a448-0c4ed64f2816
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# MDVA-34330 : Commandes non filtrées selon le fuseau horaire de l’administrateur

Le correctif MDVA-34330 résout le problème en raison duquel les commandes ne sont pas filtrées selon le fuseau horaire de l’administrateur. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.24 est installée. L’ID de correctif est MDVA-34330. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (tous les types de déploiement) 2.3.1 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes ne sont pas filtrées en fonction du fuseau horaire de l’administrateur.

<u>Étapes à reproduire</u>:

1. Accédez à **Magasins** > Paramètres > **Configuration** > **Général** et définissez la variable **Fuseau horaire** to *Heure normale de l’Est (Amérique/New_York)*
1. Passer une nouvelle commande après 00h00 UTC
1. Accédez à **Ventes** > **Commandes** et filtrer selon la date du jour


<u>Résultats attendus</u>:

La commande passée aujourd’hui après 00h00 UTC est visible dans les résultats filtrés.

<u>Résultats réels</u>:

L’ordre est absent des résultats filtrés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
