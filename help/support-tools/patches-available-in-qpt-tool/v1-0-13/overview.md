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

1. **MCP-87** : meilleur temps d’indexation pour les indexeurs de produits de catégorie et de stock pour les profils volumineux.
1. **MDVA-13203** : correction du problème en raison duquel l’erreur *Integrity contrainte de violation search_tmp_ table* s’affichait après une réindexation complète.
1. **MDVA-19391** : correction d’un problème en raison duquel `analytics_collect_data` renvoyait une erreur en raison d’enregistrements de description NULL dans la table `catalog_category_entity_text`.
1. **MDVA-20376** : corrige le problème avec l’erreur *Aucune entité de ce type avec customerId = 1* dans `exception.log` pour les clients connectés après l’emplacement de la commande.
1. **MDVA-22150** : résolution du problème qui empêchait les clients ayant un produit configurable dans le panier et un coupon appliqué de se connecter si ce produit configurable était désactivé dans l’administrateur.
1. **MDVA-23426** : résolution du problème en raison duquel les emails de notification envoyés par Adobe Commerce contenaient un corps vide avec du contenu ajouté en pièce jointe.
1. **MDVA-23764** : corrige le bogue dans `JsFooterPlugin.php` qui affecte l’affichage des blocs dynamiques.
1. **MDVA-30858** : corrige le problème en raison duquel les [!DNL PayPal] rapports de règlement n’étaient pas disponibles sous **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** accord comme prévu.
1. **MDVA-32545** : correction d’un problème en raison duquel les factures ne sont pas envoyées automatiquement lors de la création de commandes de la part de l’administrateur.
1. **MDVA-32714** : correction d’un problème en raison duquel le prix du groupe de clients ne fonctionnait pas dans la requête de produit GraphQL.
1. **MDVA-33106** : résolution du problème d’effacement des modifications de produit reprogrammées après l’exécution de la commande cron `run`.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
