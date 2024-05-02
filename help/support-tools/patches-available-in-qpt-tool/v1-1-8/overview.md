---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.8'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.8.
exl-id: a203d482-fdfc-406a-87e8-2a650ebb34b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.8 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.8.

QPT v1.1.8 comprend les correctifs suivants :

1. **MDVA-38393**: corrige le problème en raison duquel les règles du catalogue ne fonctionnaient plus pour un produit configurable si son produit simple était renommé.
1. **MDVA-39153**: correction d’un problème en raison duquel un montant de remise n’était pas correctement calculé lors d’une réorganisation dans l’Admin.
1. **MDVA-41139**: correction d’un problème en raison duquel les produits configurables étaient en rupture de stock après l’importation du produit lorsqu’une quantité=0 d’un produit simple était utilisée pour l’une de ses sources.
1. **MDVA-41215**: corrige le problème en raison duquel les utilisateurs obtenaient l’erreur 500 après avoir défini la variable *mage-messages* s’il existe déjà, mais qu’il n’y a aucun nouveau message.
1. **MDVA-42326**: correction d’un problème en raison duquel les clients obtenaient une erreur lors de l’extraction après un délai d’expiration de session, même si le panier persistant était activé.
1. **MDVA-42341**: corrige le problème en raison duquel la variable `categoryList` La requête GraphQL ne filtre pas les résultats si une requête comporte l’en-tête Magasin .

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
