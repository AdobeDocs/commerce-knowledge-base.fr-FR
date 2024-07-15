---
title: 'MDVA-30858 : Rapports du règlement PayPal manquants'
description: "Le correctif MDVA-30858 corrige l’absence de rapports de règlement PayPal lorsque plusieurs comptes PayPal sont présents. Les rapports doivent être disponibles sous Admin sidebar &gt; **Reports** &gt; Sales &gt; **PayPal Agreement**. Au lieu de cela, le message : *Nous n'avons trouvé aucun enregistrement.* s’affiche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858 : Les rapports de règlement PayPal sont manquants

Le correctif MDVA-30858 corrige l’absence de rapports de règlement PayPal lorsque plusieurs comptes PayPal sont présents. Les rapports doivent être disponibles sous la barre latérale d’administration > **Rapports** > Ventes > **Règlement PayPal**. Au lieu de cela, le message : *Nous n&#39;avons trouvé aucun enregistrement.* s’affiche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction du problème en raison duquel aucun enregistrement n’était trouvé dans **Rapports** > Ventes > **Règlement PayPal** lors de la présence de plusieurs comptes PayPal.

<u>Étapes à reproduire</u> :

1. Configurez les rapports de règlement PayPal.
1. Accédez à Admin, à **Rapports** > Ventes > **Règlement PayPal**.
1. Pour les mises à jour les plus récentes, cliquez sur **Récupérer les mises à jour** dans le coin supérieur droit.

<u>Résultats attendus</u> :

Les rapports doivent s’afficher.

<u>Résultats réels</u> :

Aucun élément n’apparaît dans la grille, bien que les rapports soient disponibles.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
