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

1. **ACSD-45168**: corrige le problème en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits qui contiennent des *url_key* attributs remplacés au niveau de l’affichage du magasin.
1. **ACSD-46617**: corrige le problème en raison duquel la variable **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au nombre configuré *Montant minimal de la commande*.
1. **ACSD-46770**: corrige le problème d’envoi des emails de l’ordre d’administration même lorsque la variable *Confirmation de commande par e-mail* n’est pas cochée.
1. **ACSD-46865**: corrige le problème en raison duquel la variable [!UICONTROL Shipment and Credit Memo] La grille n’est pas renseignée lorsque l’indexation asynchrone est activée.
1. **ACSD-47004**: correction d’un problème en raison duquel la TVA n’était pas appliquée à une adresse de facturation sans identifiant de TVA.
1. **ACSD-47079**: corrige le problème en raison duquel l’état du stock des produits composites (regroupés, configurables) n’était pas mis à jour lorsque l’état du stock des sous-produits changeait via le POST API REST /rest/V1/inventory/source-items.
1. **ACSD-47137**: améliore la vitesse de chargement de la galerie d’images lorsque le dossier pub/média est très volumineux.
1. **ACSD-47336**: correctifs *Quelque chose s&#39;est mal passé.* lors de l’affichage des notifications dans l’administrateur Commerce.
1. **ACSD-47559**: correction d’un problème en raison duquel la zone Prévisualiser le modèle de courrier électronique n’était pas entièrement visible.
1. **ACSD-47803**: corrige le problème d’affichage des échantillons de produits configurables en rupture de stock selon la disponibilité.
1. **ACSD-47920**: corrige le problème en raison duquel les commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même lorsque la variable *Autoriser le passage en caisse des invités* est désactivé.
1. **ACSD-47955**: correction d’un problème en raison duquel GraphQL n’affichait pas correctement la remise au panier.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
