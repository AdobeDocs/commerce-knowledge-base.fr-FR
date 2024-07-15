---
title: La pagination du catalogue ne fonctionne pas avec Elasticsearch 6.x
description: Cet article fournit un correctif pour le problème Adobe Commerce où la pagination de catalogue ne fonctionne pas sur Elasticsearch 6.x.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# La pagination du catalogue ne fonctionne pas avec Elasticsearch 6.x

Cet article fournit un correctif pour le problème Adobe Commerce où la pagination de catalogue ne fonctionne pas sur Elasticsearch 6.x.

Le correctif ci-dessous résout les problèmes que les utilisateurs d’Adobe Commerce 2.3.3 rencontrent dans les déploiements où Elasticsearch 6.x est utilisé comme moteur de recherche de catalogue. Un message d’erreur s’affiche lorsque les utilisateurs tentent de parcourir la première page des résultats de recherche.

Une fois ce correctif installé, les utilisateurs pourront parcourir tous les résultats de la recherche.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.3
* Adobe Commerce on-premise 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Problème

Un problème a été détecté dans Magento Open Source, Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud où la pagination de la page des résultats de recherche ne fonctionne pas si vous changez de page.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce.
1. Activez Elasticseach 6 comme moteur de recherche catalogue.
1. Ajoutez un certain nombre de produits à la catégorie qui vont au-delà de la limite de 1 page définie dans l’administrateur. **Remarque** : 12 est le nombre par défaut de produits affichés par page dans Adobe Commerce 2.3.3.
1. Ouvrez Catégorie sur le storefront (résultats de recherche ou page de catégorie) et accédez à la page 2.

<u>Résultat attendu</u> :

Les produits doivent s’afficher sur la deuxième page.

<u>Résultat réel</u> :

**&quot;***Nous ne pouvons pas trouver de produits correspondant au message de sélection***&quot;** s’affiche sur la deuxième page.

## Solution

Pour résoudre le problème, appliquez le correctif joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[ Problème de pagination du catalogue sur le correctif Elasticsearch 6.x ](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - Le correctif est compatible avec toutes les versions et éditions concernées.

>[!WARNING]
>
>Adobe recommande vivement d&#39;appliquer le correctif dès que possible, même si vous n&#39;avez présenté aucun symptôme.

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
