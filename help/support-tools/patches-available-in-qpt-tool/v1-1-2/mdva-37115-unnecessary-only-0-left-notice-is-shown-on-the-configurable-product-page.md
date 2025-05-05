---
title: '"MDVA-37115 : un avis "Seulement 0 à gauche" s’affiche sur la page du produit"'
description: Le correctif MDVA-37115 résout le problème en raison duquel l’avis inutile *Seul 0 gauche* s’affiche sur la page du produit configurable. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-37115. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 08aa6ac7-13ae-44c1-9db4-d449c3d8c985
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-37115 : un avis &quot;Seulement 0 gauche&quot; s’affiche sur la page du produit.

Le correctif MDVA-37115 résout le problème en raison duquel l’avis inutile *Uniquement 0 left* s’affiche sur la page du produit configurable. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-37115. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un avis *Seul 0 gauche* superflu s’affiche sur la page du produit configurable.

<u>Conditions préalables</u> :

Les modules d’inventaire sont installés.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec peu d’options.
1. Allez au front-end.
1. Ouvrez la page de produit configurable et sélectionnez n’importe quelle option.

<u>Résultats attendus</u> :

Aucun avis *Seul 0 de gauche* s’affiche sur la page du produit.

<u>Résultats réels</u> :

*Seul 0 de gauche* s’affiche sur la page du produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
