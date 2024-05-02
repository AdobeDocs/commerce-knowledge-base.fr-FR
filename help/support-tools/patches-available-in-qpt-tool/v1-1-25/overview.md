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

1. **ACSD-47292**: corrige le problème en raison duquel les produits groupés en rupture de stock ne sont pas disponibles dans la réponse GraphQL si la variable *afficher les produits en rupture de stock* est défini sur *Oui*.
1. **ACSD-47520**: corrige le problème en raison duquel les clients perdent des points de récompense lors de la création d’une note de crédit.
1. **ACSD-47910**: corrige le problème des commandes, factures, envois et notes de crédit manquants dans les grilles d’entités respectives.
1. **ACSD-48044**: correction d’un problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêchait le placement des commandes.
1. **ACSD-48058**: correction d’un problème en raison duquel la réindexation des prix du produit ne fonctionnait pas si le produit du lot n’était affecté à aucun site web.
1. **ACSD-48234**: corrige le problème en raison duquel le résultat de la recherche catalogue affichait un nombre d’éléments de catégorie incorrect lorsque la variable *Afficher en rupture de stock* est activée.
1. **ACSD-48262**: corrige le problème en raison duquel les produits ne sont pas visibles sur le front-end lors de la *[!UICONTROL Allow All Products Per Page]* est défini sur *Oui*.
1. **ACSD-48293**: corrige le problème de rupture de stock des produits composites lorsque les produits enfants qui ont été vendus sont retrouvés en stock.
1. **ACSD-48300**: corrige le problème qui empêchait la création d’un retour en cas de suppression du produit configurable.
1. **ACSD-48313**: corrige le problème en raison duquel la variable *configurable_variations* n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour *additional_attributes*.
1. **ACSD-48627**: résout le problème en raison duquel le produit configurable en rupture de stock provoquait une erreur lors de l’envoi d’une demande GraphQL pour obtenir les détails du panier.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
