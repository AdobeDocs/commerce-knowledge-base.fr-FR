---
title: "MDVA-34928 : erreur de page de passage en caisse après suppression du crédit de magasin"
description: Le correctif MDVA-34928 résout le problème en raison duquel, après la suppression du crédit de magasin, un chargeur infini se trouve sur la page de passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-34928. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6.
exl-id: 9ef6777a-88c8-4fed-a296-0cb4e6ad153a
feature: Checkout, Orders, Returns, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-34928 : erreur de page de passage en caisse après suppression du crédit de magasin

Le correctif MDVA-34928 résout le problème en raison duquel, après la suppression du crédit de magasin, un chargeur infini se trouve sur la page de passage en caisse. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.19 est installée. L’ID de correctif est MDVA-34928. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir supprimé le crédit de magasin, un chargeur infini se trouve sur la page de passage en caisse.

<u>Étapes à reproduire</u>:

1. Créez un compte client.
1. Déterminer un article à ajouter au panier : notez le prix.
1. Modifiez le compte dans l’Admin.
1. Cliquez sur **Crédit de la boutique**.
1. Ajoutez un montant pour couvrir le prix de l’article.
1. Connectez-vous en tant que client sur le storefront.
1. Ajoutez l’élément au panier.
1. Passez à la caisse.
1. Appliquez le crédit de la boutique.
1. Essayez de supprimer le crédit de la boutique.

<u>Résultats attendus</u>:

Le crédit de magasin est supprimé.

<u>Résultats réels</u>:

Le chargeur illimité tourne jusqu’à ce que la page soit actualisée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
