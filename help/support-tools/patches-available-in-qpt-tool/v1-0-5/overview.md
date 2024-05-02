---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.0.5'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.5.
exl-id: 439358e8-d6bc-4d35-aee1-f4fc33ae267c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) Présentation de la version 1.0.5

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.5.

QPT v1.0.5 comprend les correctifs suivants :

1. **MDVA-28191**: correction d’un problème en raison duquel aucun mode de paiement n’était chargé lors de la création de la commande via l’administrateur.
1. **MDVA-28409**: corrige le problème en raison duquel la variable `sales_clean_quotes` la tâche cron échoue avec *out de mémoire* lorsque le nombre de guillemets expirés dans la base est énorme.
1. **MDVA-28661**: correction d’un problème en raison duquel une erreur était générée dans la section du compte de société Utilisateurs de l’entreprise après modification de l’administrateur de l’entreprise.
1. **MDVA-28763**: correction d’un problème en raison duquel l’image du produit était dupliquée après la mise à jour des informations sur le produit à l’aide de l’API REST plusieurs fois.
1. **MDVA-29042**: corrige le problème en raison duquel les autorisations du catalogue étaient modifiées en *Autoriser* automatiquement après l’ajout d’un nouveau produit au catalogue partagé.
1. **MDVA-29959**: corrige le problème en raison duquel un utilisateur administrateur restreint avec *Entreprises* Les autorisations ne sont pas autorisées pour supprimer le compte de la société.
1. **MDVA-30107**: corrige le problème en raison duquel le sélecteur de magasin ne fonctionnait pas comme prévu si différentes URL de base étaient utilisées pour les vues de magasin.
1. **MDVA-30265**: correction d’un problème en raison duquel le lien de suivi des envois ne fonctionnait plus après la création d’une facture.
1. **MDVA-30284**: corrige le problème d’échec de l’indexeur de recherche catalogue en raison de ce qui suit : *[!DNL Elasticsearch]erreur : la limite du nombre total de champs dans l&#39;index a été dépassée.*
1. **MDVA-30428**: correction d’un problème en raison duquel les clients ne pouvaient pas ajouter un produit à une liste bloquée si ce produit était affecté à une source d’inventaire personnalisée.
1. **MDVA-30593**: corrige le problème en raison duquel les guillemets qui ont expiré selon le paramètre Durée de vie des guillemets ne sont pas nettoyés.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
