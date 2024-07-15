---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.24.
exl-id: 7c296124-c9ae-4b7c-b711-fc39741cabe2
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.24 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.24.

QPT v1.1.24 comprend les correctifs suivants :

1. **ACSD-45168** : résolution du problème de non-génération d’URL compatibles avec l’optimisation pour les moteurs de recherche pour les produits dont les attributs *url_key* ont été remplacés au niveau de l’affichage de magasin.
1. **ACSD-46617** : correction d’un problème en raison duquel le bouton **[!UICONTROL Continue to Checkout]** était grisé même si le sous-total était supérieur au *Montant minimum de la commande* configuré.
1. **ACSD-46770** : résolution du problème d’envoi des emails de commande d’administrateur même lorsque la *confirmation de commande d’email* est décochée.
1. **ACSD-46865** : correction d’un problème en raison duquel la grille [!UICONTROL Shipment and Credit Memo] n’était pas renseignée lorsque l’indexation asynchrone était activée.
1. **ACSD-47004** : résolution du problème de non-application de la TVA à une adresse de facturation sans identifiant de TVA.
1. **ACSD-47079** : résolution du problème en raison duquel l’état du stock des produits composites (groupés, regroupés et configurables) n’est pas mis à jour lorsque l’état du stock des sous-produits change via le POST API REST /rest/V1/inventory/source-items.
1. **ACSD-47137** : améliore la vitesse de chargement de la galerie d’images lorsque le dossier pub/media est très volumineux.
1. **ACSD-47336** : corrige *un problème s’est produit.* erreur lors de l’affichage des notifications dans l’administrateur Commerce.
1. **ACSD-47559** : correction d’un problème en raison duquel la zone Modèle de prévisualisation des emails n’était pas entièrement visible.
1. **ACSD-47803** : résolution du problème d’affichage des échantillons de produits configurables en rupture de stock selon la disponibilité.
1. **ACSD-47920** : correction d’un problème en raison duquel les commandes pouvaient être passées via l’API REST en tant qu’utilisateur invité même lorsque l’option *Autoriser le passage en caisse* était désactivée.
1. **ACSD-47955** : correction d’un problème en raison duquel GraphQL n’affichait pas correctement la remise au panier.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
