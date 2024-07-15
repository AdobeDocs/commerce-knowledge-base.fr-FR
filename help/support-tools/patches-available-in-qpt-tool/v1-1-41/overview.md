---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.41'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.41.
feature: Tools and External Services
role: Admin, Developer
exl-id: 0040fd03-6e53-4e64-b3dc-997e60fabb8c
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.41

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.41.

QPT v1.1.41 comprend les correctifs suivants :

1. **ACSD-54376** : corrige le problème qui se produit dans le panier lorsqu’un produit est supprimé du catalogue partagé après avoir été ajouté au panier.
1. **ACSD-53722** : résolution du problème en raison duquel le prix des options de produit groupées passe à 0 $ lorsque des mises à jour planifiées pour différentes portées deviennent actives.
1. **ACSD-53643** : correction d’un problème en raison duquel le total de la commande était incorrect lors du placement d’une commande avec des produits désactivés ou en rupture de stock. Elle est corrigée en masquant le bouton *[!UICONTROL Place Order]* pour ces commandes.
1. **ACSD-54067** : résolution du problème de lecture d’une vidéo de produit sur un appareil mobile.
1. **ACSD-55414** : améliore les performances lorsque la MariaDB tente de convertir l’entity_id du fichier EAV de chaîne en entier.
1. **ACSD-51819** : résolution du problème de placement de plusieurs commandes avec le même ID de guillemet.
1. **ACSD-53118** : résolution du problème d’application de *[!UICONTROL Cart Price Rule]* à l’aide du code de bon alors que le produit a un attribut vide.
1. **ACSD-54324** : correction d’un problème en raison duquel la requête request_lists de GraphQL ne prenait pas en compte les paramètres de pagination et renvoyait tous les résultats.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
