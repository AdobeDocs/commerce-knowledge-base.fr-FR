---
title: "MDVA-34867 : valeurs du champ de condition pour la mise à jour planifiée non enregistrée"
description: Le correctif MDVA-34867 résout le problème en raison duquel la valeur de la condition dans la nouvelle mise à jour du planning n’est pas enregistrée lors de la modification d’une règle de prix de catalogue. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867 : Valeurs du champ de condition pour la mise à jour planifiée non enregistrées

Le correctif MDVA-34867 résout le problème en raison duquel la valeur de la condition dans la nouvelle mise à jour du planning n’est pas enregistrée lors de la modification d’une règle de prix de catalogue. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur de la condition dans la nouvelle mise à jour du planning n’est pas enregistrée lors de la modification d’une règle de prix de catalogue.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur.
1. Créez une **règle de catalogue** avec **condition** = &quot;*la catégorie est 1*&quot;.
1. Planifiez une mise à jour avec une date de début à l’avenir (par exemple : demain), définissez **Condition** = &quot;*La catégorie est 2, 3*&quot;, puis enregistrez la mise à jour.
1. Cliquez sur **Afficher/Modifier** pour la mise à jour créée ci-dessus et vérifiez les champs de condition.

<u>Résultats attendus</u> :

La **règle de catalogue** **condition** = &quot;*catégorie est 2, 3*&quot;, comme prévu.

<u>Résultats réels</u> :

La **règle de catalogue** **condition** = &quot;*catégorie est 1*&quot;, ce qui signifie que la mise à jour n’a pas été enregistrée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
