---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13 comprend les correctifs suivants :

1. **MCP-87**: amélioration du temps d’indexation pour les indexeurs de produits de catégorie et de stock pour les profils volumineux.
1. **MDVA-13203**: corrige le problème en raison duquel la variable *Intégrité contrainte violation search_tmp_table* s’affiche après une réindexation complète.
1. **MDVA-19391**: résout le problème en raison duquel `analytics_collect_data` renvoie une erreur en raison d’enregistrements de description NULL dans la variable `catalog_category_entity_text` table.
1. **MDVA-20376**: corrige le problème avec la variable *Aucune entité de ce type avec customerId = 1* dans la variable `exception.log` pour les clients connectés après l’emplacement de la commande.
1. **MDVA-22150**: correction d’un problème en raison duquel les clients disposant d’un produit configurable dans le panier et d’un bon appliqué ne pouvaient pas se connecter si ce produit configurable était désactivé dans l’administrateur.
1. **MDVA-23426**: corrige le problème en raison duquel les emails de notification envoyés par Adobe Commerce contenaient un corps vide avec du contenu ajouté en tant que pièce jointe.
1. **MDVA-23764**: corrige le bogue dans `JsFooterPlugin.php` qui affecte l&#39;affichage des blocs dynamiques.
1. **MDVA-30858**: corrige le problème avec [!DNL PayPal] Les rapports de règlement ne sont pas disponibles sous **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** Accord comme prévu.
1. **MDVA-32545**: correction d’un problème en raison duquel les factures ne sont pas envoyées automatiquement lors de la création de commandes de la part de l’administrateur.
1. **MDVA-32714**: correction d’un problème en raison duquel le prix du groupe de clients ne fonctionnait pas dans la requête de produit GraphQL.
1. **MDVA-33106**: corrige le problème en raison duquel les modifications de produit reprogrammées sont effacées après le cron. `run` est exécutée.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
