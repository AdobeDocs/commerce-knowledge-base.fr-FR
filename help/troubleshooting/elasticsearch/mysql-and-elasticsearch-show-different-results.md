---
title: MySQL et Elasticsearch affichent des résultats différents
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.3 lié à l’obtention de différents résultats de recherche pour la même requête de recherche avec MySQL et Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL et Elasticsearch affichent des résultats différents

>[!WARNING]
>
> [Le moteur de recherche de catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). L’hôte Elasticsearch doit être configuré et configuré avant d’installer la version 2.4.0. Voir [Installation et configuration de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) dans notre documentation destinée aux développeurs.

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.3 lié à l’obtention de différents résultats de recherche pour la même requête de recherche avec MySQL et Elasticsearch.

## Problème :

Les résultats de recherche de votre catalogue avec le même jeu de filtres diffèrent selon le moteur de recherche utilisé, MySQL ou Elasticsearch.

<u>Étapes à reproduire</u> :

1. Installez et configurez Elasticsearch.
1. Sur le storefront, sélectionnez l’un des filtres.
1. Notez le nombre de produits correspondants.
1. Configuration de la valeur par défaut [Recherche MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Sur le storefront, sélectionnez l’un des filtres.
1. Notez le nombre de produits correspondants.

<u>Résultat attendu</u>: le nombre de produits correspondants est le même.

<u>Résultat réel</u>: le nombre de produits correspondants est différent.

## Correctif

Les correctifs sont joints à cet article. Pour télécharger un correctif, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom de fichier requis, ou cliquez sur les liens suivants :

[Téléchargez MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch.](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[Téléchargez MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch.](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Versions Adobe Commerce compatibles :

Les correctifs ont été créés pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.3 (le `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` fichier)
* Adobe Commerce sur l’infrastructure cloud 2.2.6 (le `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` fichier)

La variable `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.4
* Adobe Commerce sur l’infrastructure cloud 2.2.5
* Adobe Commerce on-premise 2.2.3
* Adobe Commerce on-premise 2.2.4
* Adobe Commerce On-Premise 2.2.5

La variable `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce on-premise 2.2.6

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
