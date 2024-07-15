---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.0.20'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.20.
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.20 - Aperçu

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.0.20.

QPT v1.0.20 comprend les correctifs suivants :

1. **MC-41359** : résolution du problème des paramètres de cookie SameSite incorrects.
1. **MDVA-11189** : corrige le problème lors de l’importation d’un fichier CSV pour mettre à jour le stock de produits. Les lignes de la table `cataloginventory_stock` sont supprimées.
1. **MDVA-15546** : corrige le problème en raison duquel, après la création d’une commande, une erreur *Column entity_id où clause est ambigüe* s’affiche dans le journal des exceptions.
1. **MDVA-19640** : résolution du problème où [!DNL Advanced Reporting] n’affiche aucune donnée.
1. **MDVA-21095** : corrige le problème lorsqu’une requête `INSERT INTO search_tmp` ne se terminera pas après la mise à jour de la valeur d’attribut de masse.
1. **MDVA-22026** : corrige le problème d’échec de l’importation de produits à partir d’un fichier CSV incluant des images à partir d’URL externes.
1. **MDVA-22383** : correction d’un problème en raison duquel l’enregistrement d’un produit prend beaucoup de temps et que la page se casse.
1. **MDVA-23845** : correction d’un problème en raison duquel les modèles d’email ne pouvaient pas être prévisualisés une fois la minification JavaScript activée.
1. **MDVA-26639** : résolution du problème de création d’un modèle d’email de confirmation de commande en raison duquel les éléments de commande sont manquants dans le courrier de commande.
1. **MDVA-33168** : corrige le problème lors de la mise à jour d’un attribut de produit via l’API, tous les autres attributs deviennent une valeur vide.
1. **MDVA-36170** : Ceci corrige le problème en raison duquel la requête GraphQL n’est pas mise en cache à l’aide de la balise de cache de catégorie.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
