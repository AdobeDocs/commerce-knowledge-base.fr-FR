---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.12'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.12.
exl-id: 749dbfd5-9ded-4919-8c57-0f66c85751e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.12 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.12.

QPT v1.1.12 comprend les correctifs suivants :

1. **MDVA-39546** : correction d’un problème en raison duquel la date de début de la mise à jour intermédiaire pouvait être définie sur une date antérieure à la date actuelle lors de la modification.
1. **MDVA-39713** : correction d’un problème en raison duquel l’utilisateur était en mesure de modifier l’heure de début d’une mise à jour planifiée active.
1. **MDVA-3993** : corrige le problème en raison duquel les modifications d’inventaire effectuées par le biais de l’API ne sont pas répercutées sur la page du produit sur le front-end.
1. **MDVA-41136** : corrige le problème en raison duquel la date d’expiration de `mage-cache-sessid` n’est pas étendue, ce qui entraîne un nettoyage des données client.
1. **MDVA-41229** : corrige le problème en raison duquel les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables.
1. **MDVA-41628** : correction du problème en raison duquel les utilisateurs administrateurs limités existants avaient accès aux nouvelles ressources lors de l’ajout de nouveaux modules.
1. **MDVA-42410** : correction d’un problème en raison duquel les rapports de coupon n’affichaient que la devise de base par défaut.
1. **MDVA-42645** : correction d’un problème en raison duquel l’administrateur ne pouvait pas rembourser les points de récompense si la fonctionnalité de crédit de magasin était désactivée.
1. **MDVA-42689** : corrige le problème qui entraînait une *violation de contrainte d’intégrité* lors de la mise à jour de catégories de produits lors de l’importation.
1. **MDVA-42855** : correction d’un problème en raison duquel une nouvelle adresse client n’était pas enregistrée dans le carnet d’adresses lors de l’extraction.
1. **MDVA-42950** : corrige le problème de lecture des vidéos sur la page du produit.
1. **MDVA-43232** : correction du problème en raison duquel le tri des produits dans [!DNL Visual Merchandiser] par prix spécial en bas/haut générait une erreur lors de l’enregistrement de la catégorie.
1. **MDVA-43348** : corrige le problème en raison duquel la demande GraphQL de carte-cadeau affichait une erreur si `gift_card_options` contenait *uid*.
1. **MDVA-43414** : corrige l’erreur fatale PHP qui se produit lors de l’exécution du consommateur de file d’attente `inventory.reservations.updateSalabilityStatus` sur des SKU numériques.
1. **MDVA-43726** : corrige le problème en raison duquel la règle de prix du catalogue basée sur la correspondance d’attributs au niveau du magasin ne s’appliquait pas après une réindexation partielle.
1. **MDVA-43731** : corrige le problème en raison duquel les *Synonymes de recherche* ne fonctionnent plus lorsque la valeur est ajoutée dans *Termes minimum à correspondre*.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
