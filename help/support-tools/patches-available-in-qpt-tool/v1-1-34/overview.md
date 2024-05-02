---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.34

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34 comprend les correctifs suivants :

1. **ACSD-52277**: correction d’un problème en raison duquel un utilisateur administrateur n’était pas redirigé correctement après avoir sélectionné la vue de magasin lors de la création d’une commande dans l’administrateur.
1. **ACSD-50813**: corrige le problème lorsqu’un administrateur ne peut pas ajouter de produits regroupés contenant une barre oblique dans le SKU avec la variable [!UICONTROL Add Products by SKU] à l’ordre d’administration.
1. **ACSD-51630**: correction d’un problème en raison duquel un grand nombre de messages système ralentissait le téléchargement des pages d’administration.
1. **ACSD-51853**: corrige le problème en raison duquel les styles de texte copiés ne sont pas appliqués lors de l’utilisation de [!DNL Page Builder].
1. **ACSD-52160**: corrige le problème en raison duquel le résultat de la validation d’un produit par rapport à la règle de prix du panier n’était pas correctement évalué, en fonction de la condition de la règle. *Si un élément est TROUVÉ/INTROUVABLE dans le panier avec toutes/toutes ces conditions vraies*.
1. **ACSD-51636**: correction d’un problème en raison duquel un administrateur ne pouvait pas ajouter de nouveaux utilisateurs à partir de la section du compte client, même s’il disposait de tous les rôles et autorisations nécessaires.
1. **ACSD-51739**: corrige le problème en raison duquel une erreur était renvoyée lorsque la variable `structure_id` est demandé dans une `CompanyTeam` Requête GraphQL.
1. **ACSD-51857**: corrige le problème de lenteur des performances de `aggregate_sales_report_bestsellers_data` le rapport cron affecte volumineux `sales_order` et `sales_order_item` tables de base de données.
1. **ACSD-48448**: corrige un problème de condition de concurrence survenant lors des annulations de commande, qui entraînait la duplication de l’entrée dans la variable *inventory_reservation* table.
1. **ACSD-52689**: correction d’un problème en raison duquel les images ne pouvaient pas être téléchargées vers [!DNL Amazon S3] stockage à l’aide de l’API REST.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
