---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.30'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.30.
exl-id: 40b1bb88-5032-4c56-ae32-99f55df12652
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.30

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.30.

QPT v1.1.30 comprend les correctifs suivants :

1. **ACSD-50336**: corrige le problème en raison duquel les emails d’alerte de produit ne sont pas envoyés lorsqu’un produit est à nouveau en stock ou que le prix est modifié.
1. **ACSD-50367**: corrige le problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lors de la création d’un attribut d’adresse du client à sélection multiple sans valeurs.
1. **ACSD-49877**: corrige le problème de non-fonctionnement de la lecture automatique de la vidéo sur mobile. [!DNL Safari] lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de diffusion en continu.
1. **ACSD-50165**: corrige l’erreur *Le fichier ne peut pas être supprimé. Warning!unlink : aucun fichier ou répertoire de ce type lors de la purge du cache JS/CSS de l’administrateur.*.
1. **ACSD-49737**: corrige le problème de marquage incorrect d’un coupon utilisé après l’échec du paiement de la carte.
1. **ACSD-50814**: correction d’un problème qui empêchait un utilisateur administrateur de créer une note de crédit.
1. **ACSD-50116**: correction d’un problème en raison duquel un utilisateur administrateur ne pouvait pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.
1. **ACSD-49513**: corrige le problème d’échec de la synchronisation du stockage à distance en raison de fichiers de 0 octet.
1. **ACSD-46683**: corrige le problème qui entraînait l’affichage du prix d’expédition. *Pas encore calculé*.
1. **ACSD-49129**: corrige le problème en raison duquel l’attribut de contenu ([!UICONTROL base64 image code]) n’est pas renvoyé dans `rest/V1/products/sku/media` réponses de l’API de média de produit.
1. **ACSD-50276**: correction d’un problème en raison duquel le formulaire d’enregistrement du client ne fonctionnait pas sur le storefront si un attribut de client à sélection multiple était créé.
1. **ACSD-50527**: corrige l’erreur qui se produit lors de l’enregistrement d’une page avec un bloc dynamique vide.
1. **ACSD-49973**: améliore les performances de récupération des produits regroupés via GraphQL.
1. **ACSD-51114**: correction d’un problème en raison duquel un produit aléatoire disparaissait des catalogues volumineux lorsque l’indexation asynchrone était activée. Améliore les performances de la réindexation asynchrone pour les catalogues volumineux.
1. **B2B-2598**: ajoute la fonctionnalité de mise en cache au `availableStores`, `countries`, `country`, `currency`, et `storeConfig` Requêtes GraphQL.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
