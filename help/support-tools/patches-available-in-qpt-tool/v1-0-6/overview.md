---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.0.6'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.6.
exl-id: 38e9454b-e278-4b14-a861-2af0623db92e
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) Présentation de la version 1.0.6

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.6.

QPT v1.0.6 comprend les correctifs suivants :

1. **MDVA-28202**: corrige le problème en raison duquel la navigation par calques ne filtrait pas correctement les produits configurables lorsque MSI est utilisé.
1. **MDVA-28300**: corrige le problème en raison duquel la demande GQL ne reflétait pas les modifications de prix des règles de prix du catalogue.
1. **MDVA-28993**: met en oeuvre la variable *La valeur minimale doit correspondre* fonctionnalité et recherche partielle [!DNL Elasticsearch] moteur. Résout les problèmes liés aux tirets dans les requêtes de recherche.
1. **MDVA-29446**: corrige le problème en raison duquel le prix de la méthode d’expédition non applicable s’affichait comme zéro pendant le passage en caisse.
1. **MDVA-29787**: corrige le problème en raison duquel la règle de ciblage pour les produits associés ne fonctionnait pas lorsque *est l’un des* est utilisée pour définir les produits à afficher.
1. **MDVA-30102**: résout le problème en raison duquel [!DNL Redis] Le cache augmente rapidement, car les caches de mise en page n’ont pas de durée de vie (TTL).
1. **MDVA-30357**: corrige le problème lié à la création d’URL d’image incorrectes lors de la génération d’un plan de site par cron.
1. **MDVA-30565**: résout le problème en raison duquel *Aucune entité de ce type avec cartid = 0* s’affiche pour les clients invités lors du passage en caisse en storefront si le panier persistant est activé.
1. **MDVA-30599**: correction d’un problème en raison duquel les guillemets d’invité créés à l’aide de l’API étaient incorrectement marqués comme guillemets pour les clients connectés.
1. **MDVA-30977**: corrige le problème lié aux produits aléatoires manquants dans les catégories après la réindexation.
1. **MDVA-31006**: corrige le problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide de [!DNL Paypal Express] paiement.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
