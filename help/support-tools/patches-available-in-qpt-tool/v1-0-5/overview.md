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

# [!DNL Quality Patches Tool] (QPT) v1.0.5 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.5.

QPT v1.0.5 comprend les correctifs suivants :

1. **MDVA-28191** : corrige le problème en raison duquel aucun mode de paiement n’est chargé lors de la création de la commande via l’administrateur.
1. **MDVA-28409** : résolution du problème d’échec de la tâche `sales_clean_quotes` cron avec l’erreur *out-of-memory* lorsque le nombre de guillemets expirés dans la base de données est énorme.
1. **MDVA-28661** : correction d’un problème en raison duquel une erreur était générée dans la section du compte de société Utilisateurs de l’entreprise après modification de l’administrateur de l’entreprise.
1. **MDVA-28763** : résolution du problème de duplication de l’image du produit après mise à jour plus d’une fois des informations sur le produit à l’aide de l’API REST.
1. **MDVA-29042** : corrige le problème en raison duquel les autorisations du catalogue étaient remplacées automatiquement par *Autoriser* après l’ajout d’un nouveau produit au catalogue partagé.
1. **MDVA-29959** : corrige le problème qui empêchait un utilisateur administrateur restreint disposant d’autorisations *Entreprises* de supprimer le compte de la société.
1. **MDVA-30107** : corrige le problème en raison duquel le sélecteur de magasin ne fonctionne pas comme prévu si d’autres URL de base sont utilisées pour les vues de magasin.
1. **MDVA-30265** : résolution du problème de l’arrêt du fonctionnement du lien de suivi des envois après la création d’une facture.
1. **MDVA-30284** : résolution du problème d’échec de l’indexeur de recherche catalogue en raison de l’erreur *[!DNL Elasticsearch]suivante : la limite du nombre total de champs dans l’index a été dépassée.*
1. **MDVA-30428** : correction d’un problème en raison duquel les clients ne pouvaient pas ajouter de produit à une liste de souhaits si ce produit était affecté à une source d’inventaire personnalisée.
1. **MDVA-30593** : corrige le problème en raison duquel les guillemets qui ont expiré selon le paramètre Durée de vie des citations ne sont pas nettoyés.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
