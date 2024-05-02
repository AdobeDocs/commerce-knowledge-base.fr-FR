---
title: 'Correctif MDVA-31363 : la règle du prix du panier ne s’applique pas (GraphQL)'
description: Le correctif MDVA-31363 corrige le problème en raison duquel la règle de prix du panier avec coupon ne s’applique pas via GraphQL lorsque l’action "Remise sur le montant fixe pour le panier entier" est utilisée. Ce correctif est disponible lorsque l’outil de correctifs de qualité (QPT) 1.0.9 est installé. Le problème devrait être corrigé dans Adobe Commerce version 2.4.2.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Correctif MDVA-31363 : la règle du prix du panier ne s’applique pas (GraphQL)

>[!WARNING]
>
>Un nouveau correctif appelé MDVA-33975 corrige les problèmes de calcul des prix de GraphQL. Le MDVA-31363 est déprécié et il est recommandé d’appliquer le correctif MDVA-33975. Pour accéder à ce patch, reportez-vous à la section [Correctif MDVA-33975 : calculs des prix GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

Le correctif MDVA-31363 corrige le problème en raison duquel la règle de prix du panier avec coupon ne s’applique pas via GraphQL lorsque l’action &quot;Remise sur le montant fixe pour le panier entier&quot; est utilisée. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.9 est installée. Le problème devrait être corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.2 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Recalculer les totaux des guillemets avant de donner une réponse sur les prix entraîne la perte des règles appliquées.

<u>Étapes à reproduire</u>:

1. Créez un produit simple.
1. Créez une règle de prix de panier avec une remise fixe pour l’ensemble du panier.
1. Créez un panier à l’aide de GraphQL.
1. Enregistrez la carte\_id à partir de la réponse et ajoutez le produit de l’étape 1 au panier à l’aide de GraphQL.
1. Activez la règle de prix du panier en ajoutant le code de coupon au panier à l’aide de GraphQL.
1. Vérifiez le prix en réponse.

<u>Résultats attendus</u>:

La remise est appliquée.

<u>Résultats réels</u>:

La remise n’est pas appliquée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
