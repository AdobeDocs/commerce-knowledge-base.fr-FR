---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.4'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.4.
exl-id: b7729740-acba-457e-a296-469016c98b51
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.4 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.4.

QPT v1.1.4 comprend les correctifs suivants :

1. **MC-42528**: corrige le problème en raison duquel la variable `categoryList` La requête GraphQL renvoie les catégories affectées et non affectées.
1. **MDVA-25631**: améliore les performances pour la modification et l’enregistrement des segments de clients qui contiennent un grand nombre de clients.
1. **MDVA-26005**: correction d’un problème en raison duquel il était impossible de sélectionner une catégorie dans une arborescence de catégories pour les conditions des règles de prix du panier.
1. **MDVA-29400**: corrige le problème lié aux commandes dupliquées placées avec [!DNL PayPal Express Checkout].
1. **MDVA-37725**: corrige le problème en raison duquel les courriers électroniques de commande asynchrones envoyés à partir de sites web autres que les sites par défaut contenaient des URL de logo provenant du site web par défaut.
1. **MDVA-39482**: correction d’un problème en raison duquel un produit était en rupture de stock s’il était importé avec une quantité &quot;0&quot; lorsque les commandes en arrière-plan étaient activées.
1. **MDVA-40101**: corrige le problème en raison duquel les articles ne sont pas supprimés du mini panier après un placement de commande réussi à l’aide de [!DNL PayPal Express] Passage en caisse.
1. **MDVA-40399**: correction d’un problème en raison duquel les factures partielles d’une même commande ne pouvaient pas être créées simultanément via l’API REST.
1. **MDVA-40401**: corrige le problème en raison duquel la valeur d’utilisation des coupons changeait même si le placement d’une commande échouait.
1. **MDVA-40435**: corrige le problème lié à une remise incorrecte sur les produits en bundle avec des prix dynamiques lorsqu’ils sont appliqués via GraphQL.
1. **MDVA-40537**: correction d’un problème en raison duquel les utilisateurs obtenaient une erreur lors de la création d’une vue de magasin s’il existait plusieurs pages CMS avec la même clé d’URL.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
