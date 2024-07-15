---
title: "MDVA-32449 : l’historique des commandes client est lent ou ne se charge pas avec l’erreur 503"
description: Le correctif MDVA-32449 résout le problème sur Adobe Commerce où l’historique des commandes client se charge lentement ou ne se charge pas et affiche une erreur 503. Il s’agit d’un problème lorsque plus de 1 300 clients sont affectés à une société B2B. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé. Veuillez noter que ce problème a été corrigé dans Adobe Commerce 2.4.1.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449 : l’historique des commandes client est lent ou ne se charge pas avec l’erreur 503

Le correctif MDVA-32449 résout le problème sur Adobe Commerce où l’historique des commandes client se charge lentement ou ne se charge pas et affiche une erreur 503. Il s’agit d’un problème lorsque plus de 1 300 clients sont affectés à une société B2B. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé. Veuillez noter que ce problème a été corrigé dans Adobe Commerce 2.4.1.

## Produits et versions concernés

Il s’agit d’un problème lorsque plus de 1 300 clients sont affectés à une société B2B.

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction d’un problème en raison duquel l’historique des commandes se charge très lentement ou ne se charge pas du tout.

<u>Conditions préalables</u> :

Plus de 13 000 clients affectés à une entreprise B2B

<u>Étapes à reproduire</u> :

1. Connectez-vous au storefront en tant qu’administrateur de l’entreprise.
1. Accédez à la page Historique des commandes client .

<u>Résultats attendus</u> :

La page de l’historique des commandes client se charge normalement.

<u>Résultats réels</u> :

La page se charge très lentement ou la page risque de ne pas se charger et une erreur de délai d’expiration s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
