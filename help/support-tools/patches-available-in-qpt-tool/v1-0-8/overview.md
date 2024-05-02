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

# [!DNL Quality Patches Tool] (QPT) Présentation de la version 1.0.8

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 comprend les correctifs suivants :

1. **MDVA-28357**: remplace l’analyseur standard par un analyseur personnalisé avec un jeton de mot-clé pour le champ SKU dans la variable [!DNL ElasticSearch] pour que les requêtes de recherche avec caractères génériques fonctionnent avec les SKU contenant un trait d’union (&quot;-&quot;).
1. **MDVA-29954**: corrige le problème en raison duquel la variable *Nouvelle demande d’enregistrement d’entreprise* et *Vous avez été lié à une société.* les emails sont envoyés à partir d’une adresse incorrecte.
1. **MDVA-30112**: résout le problème en raison duquel, si le nombre de commandes dépasse la valeur *taille du lot* , Adobe Commerce considère les commandes avec la variable *en attente* comme incohérences.
1. **MDVA-30963**: corrige le problème en raison duquel les résultats de filtrage de produits définis sur ne contenaient que les valeurs spécifiées pour la variable *Toutes les vues de magasin* dans Admin, incluez les produits dont les valeurs sont remplacées au niveau de la vue de magasin.
1. **MDVA-31150**: correction d’un problème en raison duquel les soldes des cartes de crédit et des cadeaux de la boutique n’étaient pas renvoyés par l’appel de l’API GET Invoice REST, lorsque la facture était validée par l’appel de l’API REST et que la commande était partiellement payée par les comptes de carte de crédit et de cadeau de la boutique.
1. **MDVA-31242**: corrige le problème d’affichage d’un signe de devise incorrect dans [!UICONTROL Credit Memo] grid.
1. **MDVA-31295**: corrige le problème en raison duquel les points de récompense ne sont pas calculés lorsqu’une commande partielle est terminée et que les éléments sont taxés.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
