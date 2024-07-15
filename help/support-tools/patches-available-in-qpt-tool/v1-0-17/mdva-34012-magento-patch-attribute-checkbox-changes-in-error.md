---
title: 'Correctif MDVA-34012 : la case à cocher des attributs change en erreur'
description: Le correctif MDVA-34012 résout le problème en raison duquel la case à cocher d’un attribut est modifiée après une mise à jour du planning par erreur.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Correctif MDVA-34012 : la case à cocher des attributs change en erreur

Le correctif MDVA-34012 résout le problème en raison duquel la case à cocher d’un attribut est modifiée après une mise à jour du planning par erreur.

Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.1 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Connectez-vous à Admin et accédez à **Catalogue > Produits**.
1. Modifiez n’importe quel produit simple.
1. Définissez la vue de magasin sur une vue de magasin spécifique.
1. Enregistrez le produit avec la case à cocher **Utiliser la valeur par défaut** sélectionnée pour un attribut (par exemple : **Activer le produit** ).
1. Cliquez sur **Planifier une nouvelle mise à jour** pour planifier certaines modifications (par exemple : **Price** ou **Prix spécial** pour une vue de magasin spécifique).
1. Patientez jusqu’à ce que les modifications soient terminées.
1. Vérifiez le produit. La case à cocher doit être décochée et une valeur d’attribut de magasin doit être spécifiée.

<u>Résultats attendus</u> :

La case à cocher de l’attribut doit rester la même et n’est pas modifiée après la mise à jour du planning, comme prévu.

<u>Résultats réels</u> :

La case à cocher de l’attribut est modifiée après la mise à jour du planning.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
