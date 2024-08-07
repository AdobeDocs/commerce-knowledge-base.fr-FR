---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 comprend les correctifs suivants :

1. **MDVA-29148** : corrige le problème lors de la création d’un produit via un appel API. L’attribut personnalisé de produit de type `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (multisélection par exemple) n’utilise pas sa valeur par défaut si aucune valeur n’a été fournie dans la payload.
1. **MDVA-29389** : résolution du problème lié aux rapports avancés où le `analytics_collect_data` cronjob indique : *Le port doit être configuré dans le paramètre hôte (comme localhost:3306)*.
1. **MDVA-30594** : corrige le problème qui empêchait l’enregistrement d’une commande avec plusieurs adresses lors de l’extraction lorsque FPT était configuré.
1. **MDVA-30782** : résolution du problème d’affichage du bloc dynamique, quelle que soit la règle du panier.
1. **MDVA-30815** : corrige le problème en raison duquel, lorsque vous modifiez le nombre de résultats de recherche à afficher sur la page des résultats de recherche.
1. **MDVA-30837** : ajoute des options de configuration pour le calcul de la livraison gratuite afin que l’utilisateur puisse configurer le Montant minimum de la commande pour obtenir la livraison gratuite en fonction du Sous-total (ou total général).
1. **MDVA-30945** : résolution du problème de réception d’un message d’erreur fatal lors de la mise à jour des paniers `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972** : corrige le problème en raison duquel l’état de commande personnalisée était remplacé par *Traitement* après la création d’une expédition partielle à l’aide de WebApi.
1. **MDVA-31007** : corrige le problème en raison duquel les attributs d’adresse personnalisés ne s’affichent pas correctement dans la page des détails de la commande dans la zone de mon compte et dans le serveur principal.
1. **MDVA-31021** : corrige le problème de performances dans `module-catalog-import-export/Model/Import/Product/Option.php`. S’il existe plus de ~100 000 enregistrements dans la table `catalog_product_option`, un nouveau fichier CSV avec un seul produit prend moins de 10 secondes pour être validé.
1. **MDVA-31224** : améliore les performances de l’opération de réindexation `catalog_product_price` pour les produits en bundle.
1. **MDVA-31282** : corrige le problème de double autorisation sur [!DNL Paypal PayFlow Pro] dans Adobe Commerce. Les doubles autorisations ont également pour effet de contourner les filtres de fraude [!DNL PayFlow Pro's] et de doubler les frais de transaction.
1. **MDVA-31343** : corrige le problème lié à la classe de corps supprimée `page-layout-category-full-width` lorsqu’une catégorie est planifiée.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
