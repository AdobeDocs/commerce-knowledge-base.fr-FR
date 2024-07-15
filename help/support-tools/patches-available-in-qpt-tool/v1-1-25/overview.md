---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.25'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.25.
exl-id: 49baf8c6-0a7e-40f3-bee8-fdcab3706727
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.25 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.25.

QPT v1.1.25 comprend les correctifs suivants :

1. **ACSD-47292** : corrige le problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL si l’option *Afficher les produits en rupture de stock* est définie sur *Oui*.
1. **ACSD-47520** : résolution du problème de perte de points de récompense par les clients lors de la création d’une note de crédit.
1. **ACSD-47910** : résolution du problème des commandes, factures, envois et avoirs manquants dans les grilles d’entités respectives.
1. **ACSD-48044** : correction d’un problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêchait le passage des commandes.
1. **ACSD-48058** : correction d’un problème en raison duquel la réindexation des prix du produit ne fonctionnait pas si le produit du lot n’était affecté à aucun site web.
1. **ACSD-48234** : correction d’un problème en raison duquel le résultat de la recherche catalogue affichait un nombre d’éléments de catégorie incorrect lorsque l’option *Afficher en rupture de stock* était activée.
1. **ACSD-48262** : résolution du problème en raison duquel les produits ne sont pas visibles sur l’interface lorsque le paramètre *[!UICONTROL Allow All Products Per Page]* est défini sur *Oui*.
1. **ACSD-48293** : correction d’un problème en raison duquel les produits composites étaient en rupture de stock lorsque les produits enfants qui avaient été vendus étaient retrouvés en stock.
1. **ACSD-48300** : résolution du problème de création d’un retour en cas de suppression d’un produit configurable.
1. **ACSD-48313** : résolution du problème en raison duquel la colonne *configurable_variations* n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour *additional_attributes*.
1. **ACSD-48627** : corrige le problème en raison duquel le produit configurable en rupture de stock provoquait une erreur lors de l’envoi d’une demande GraphQL pour obtenir les détails du panier.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
