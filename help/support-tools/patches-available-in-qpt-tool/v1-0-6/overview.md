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

# [!DNL Quality Patches Tool] (QPT) v1.0.6 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.6.

QPT v1.0.6 comprend les correctifs suivants :

1. **MDVA-28202** : corrige le problème en raison duquel la navigation par couches ne filtre pas correctement les produits configurables lorsque MSI est utilisé.
1. **MDVA-28300** : corrige le problème en raison duquel la demande GQL ne reflète pas les modifications de prix des règles de prix du catalogue.
1. **MDVA-28993** : met en oeuvre la fonctionnalité *Minimum doit correspondre à* et la recherche partielle pour le moteur [!DNL Elasticsearch]. Résout les problèmes liés aux tirets dans les requêtes de recherche.
1. **MDVA-29446** : correction d’un problème en raison duquel le prix de la méthode d’expédition non applicable s’affichait comme zéro lors du passage en caisse.
1. **MDVA-29787** : corrige le problème en raison duquel la règle de ciblage pour les produits associés ne fonctionne pas lorsque *est l’une des* conditions utilisées pour définir les produits à afficher.
1. **MDVA-30102** : corrige le problème en raison duquel le cache de [!DNL Redis] augmente rapidement, car les caches de mise en page n’ont pas de durée de vie (TTL).
1. **MDVA-30357** : résolution du problème de création d’URL d’image incorrectes lors de la génération d’un plan de site par cron.
1. **MDVA-30565** : correction d’un problème en raison duquel *Aucune entité de ce type avec carte = 0* ne s’affichait pour les clients invités lors du passage en caisse en magasin si le panier persistant était activé.
1. **MDVA-30599** : corrige le problème en raison duquel les guillemets d’invité créés à l’aide de l’API sont incorrectement marqués comme guillemets pour les clients connectés.
1. **MDVA-30977** : corrige le problème lié à l’absence de produits aléatoires dans les catégories après la réindexation.
1. **MDVA-31006** : corrige le problème d’affichage des commandes dupliquées après le placement d’une commande à l’aide du paiement [!DNL Paypal Express].

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
