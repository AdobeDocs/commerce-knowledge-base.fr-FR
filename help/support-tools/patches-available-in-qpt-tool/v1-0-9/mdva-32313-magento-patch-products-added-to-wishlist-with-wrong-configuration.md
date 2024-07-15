---
title: 'Correctif "MDVA-32313 : produits ajoutés à une liste bloquée avec une configuration incorrecte"'
description: Le correctif MDVA-32313 résout le problème en raison duquel les produits configurables ne peuvent pas être ajoutés correctement à la liste des souhaits, car des configurations incorrectes leur sont affectées lorsqu’ils sont ajoutés à la liste des souhaits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Correctif MDVA-32313 : produits ajoutés à une liste bloquée avec une configuration incorrecte

Le correctif MDVA-32313 résout le problème en raison duquel les produits configurables ne peuvent pas être ajoutés correctement à la liste des souhaits, car des configurations incorrectes leur sont affectées lorsqu’ils sont ajoutés à la liste des souhaits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Créez un client.
1. Connectez-vous au compte client.
1. Accédez à la page **Liste des produits** .
1. Choisissez un produit configurable (par exemple : *configurable\_1* ) et sélectionnez les options de couleur et de taille préférées sur la page **Liste de produits** (**Ne pas ouvrir la page de produits.**).
1. Cliquez sur l’icône de liste des souhaits d’un autre produit configurable (par exemple : *configurable\_2*) sur la même page sans sélectionner d’options de couleur/taille.

<u>Résultats attendus</u> :

Le produit *configurable\_2* est ajouté à la liste des souhaits sans options sélectionnées, comme prévu.

<u>Résultats réels</u> :

Le produit *configurable\_2* a été ajouté à la liste des souhaits avec la configuration du produit *configurable\_1*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
