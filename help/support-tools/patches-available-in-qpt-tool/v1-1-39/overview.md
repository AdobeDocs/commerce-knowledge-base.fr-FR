---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.39

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 comprend les correctifs suivants :

1. **ACSD-53704**: corrige le problème en raison duquel l’historique d’équilibrage des points de récompense est mal calculé après l’expiration des points de récompense.
1. **ACSD-53583**: améliore les performances de réindexation partielle pour *Produits de catégorie* et *Catégories de produits* indexeurs.
1. **ACSD-54026**: corrige un message d’erreur incorrect pour une `updateCompanyRole` Requête GraphQL pour un utilisateur non autorisé.
1. **ACSD-54106**: corrige le problème de tri des produits de catégorie par nom pour les caractères accentués turcs.
1. **ACSD-52219**: corrige le problème en raison duquel les grilles d’administration enregistrées ne fonctionnaient pas comme prévu lors du basculement fréquent entre les vues de signet.
1. **ACSD-54342**: corrige un message d’erreur incorrect *Erreur dans la structure des données : les valeurs sont mixtes* lors de l’importation d’un fichier CSV sans données valides.
1. **ACSD-54660**: ajout d’un nouvel attribut d’entrée *sort* pour trier les commandes client dans GraphQL par `sort_field` et `sort_direction`.
1. **ACSD-54776**: corrige le problème si non coché. *[!UICONTROL Use Default Value]* Les valeurs des champs de produit et autres que par défaut ne sont pas enregistrées pour le deuxième affichage de site web, de magasin et de magasin.
1. **ACSD-53998**: corrige le problème en raison duquel une erreur **[!UICONTROL Dynamic Block]** basé sur un **[!UICONTROL Customer Segment]** ne fonctionne pas correctement après la déconnexion d’un compte client.
1. **ACSD-53204**: correctifs *Le produit ne peut pas être enregistré.* erreur lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide de la fonction `rest/V1/products/<sku>/media` point de terminaison .
1. **ACSD-47657**: ajout d’un mécanisme de mise en cache pour les informations d’identification AWS. Un fournisseur d’informations d’identification utilise désormais le cache du Magento pour mettre en cache les informations d’identification extraites d’AWS pour la configuration EC2.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
