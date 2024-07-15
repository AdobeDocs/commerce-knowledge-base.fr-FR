---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 comprend les correctifs suivants :

1. **MDVA-28357** : remplace l’analyseur standard par un analyseur personnalisé avec un jeton de mot-clé pour le champ SKU dans l’index [!DNL ElasticSearch] pour que les requêtes de recherche par caractères génériques fonctionnent avec des SKU contenant un trait d’union (&quot;-&quot;).
1. **MDVA-29954** : correction d’un problème en raison duquel les *Nouvelle demande d’enregistrement de société* et *Vous avez été lié à une société* emails étaient envoyés à partir d’une adresse incorrecte.
1. **MDVA-30112** : corrige le problème en raison duquel si le nombre de commandes dépasse la valeur *bunch-size*, Adobe Commerce considère les commandes dont le statut est *en attente* comme des incohérences.
1. **MDVA-30963** : correction d’un problème en raison duquel les résultats de filtrage des produits ne contenaient que les valeurs spécifiées pour la portée *Toutes les vues de magasin* dans l’Admin, incluaient des produits dont les valeurs étaient remplacées au niveau de la vue de magasin.
1. **MDVA-31150** : correction d’un problème en raison duquel les soldes de carte-cadeau et de crédit de magasin ne sont pas renvoyés par l’appel de l’API GET Invoice Rest, lorsque la facture a été validée par l’appel de l’API REST et que la commande a été partiellement payée par les comptes de carte-cadeau et de crédit de magasin.
1. **MDVA-31242** : résolution du problème d’affichage d’un signe de devise incorrect dans la grille [!UICONTROL Credit Memo].
1. **MDVA-31295** : corrige le problème en raison duquel les points de récompense ne sont pas calculés lorsqu’une commande partielle est terminée et que les éléments sont taxés.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
