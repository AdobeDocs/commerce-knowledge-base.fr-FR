---
title: 'MDVA-34469 : mauvais code de magasin spécifié pour le panier'
description: "Le correctif MDVA-34469 résout le problème en raison duquel les utilisateurs reçoivent le message d’erreur : *Code de magasin incorrect spécifié pour le panier* lors de l’ajout d’un produit au panier après le changement d’affichage du magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 est installé. L’ID de correctif est MDVA-34469. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2."
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469 : code de magasin incorrect spécifié pour le panier

Le correctif MDVA-34469 résout le problème où les utilisateurs reçoivent le message d’erreur : *Code de magasin incorrect spécifié pour le panier* lors de l’ajout d’un produit au panier après le changement d’affichage de magasin. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.15 est installée. L’ID de correctif est MDVA-34469. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur voit une erreur de requête de panier, *&quot;Code de magasin incorrect spécifié pour le panier&quot;*, lors d’une tentative de changement de vue de magasin.

<u>Conditions préalables</u>:

* Adobe Commerce 2.4.0.
* Un site web unique avec un seul magasin et deux vues de magasin est configuré.
* Un compte client est créé.

<u>Étapes à reproduire</u>:

1. Le serveur principal Adobe Commerce est configuré pour avoir deux vues de magasin (avec les codes de magasin : par défaut, deuxième).
1. L’utilisateur crée un panier à l’aide du code de magasin par défaut.
1. L’utilisateur tente de récupérer ce panier à l’aide du deuxième code de magasin dans la variable `Store` en-tête de la requête.

<u>Résultats attendus</u>:

Le panier s’affiche car le magasin change (en envoyant le nouveau code dans la variable `Store` en-tête de demande) associe le panier au magasin demandé.

<u>Résultats réels</u>:

La requête de panier renvoie une erreur et le panier ne s’affiche pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
