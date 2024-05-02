---
title: Ai-je besoin de Fastly pour un site Adobe Commerce sans affichage ?
description: Ai-je besoin de Fastly pour un site Adobe Commerce sans affichage ?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Ai-je besoin de Fastly pour un site Adobe Commerce sans affichage ?

>[!NOTE]
>
>Tous les clients doivent utiliser Fastly pour leurs environnements de production et d’évaluation. Un réseau de diffusion de contenu (CDN) fournit rapidement des services de mise en cache, d’optimisation des images et de sécurité (DDoS et WAF) complets de page dans le cadre de votre Adobe Commerce sur les projets d’infrastructure cloud. Ces composants principaux de la solution Adobe Commerce offrent des performances et une sécurité accrues. Ces fonctionnalités font partie de la conformité PCI de l’Adobe. Vous devez configurer ces services rapides dans vos environnements de démarrage, d’évaluation, d’évaluation et de production. Si vous utilisez Adobe Commerce dans un déploiement sans interface utilisateur graphique, tout le trafic API provenant de l’Internet public doit passer par Fastly et nous vous recommandons vivement d’utiliser Fastly pour mettre en cache les réponses GraphQL. Voir [Guide du développeur de GraphQL > Mise en cache rapide](https://devdocs.magento.com/guides/v2.3/graphql/caching.html#caching-with-fastly) dans notre documentation destinée aux développeurs.

## **Question**

Je développe une mise en oeuvre sans interface d’Adobe Commerce. Dois-je toujours utiliser Fastly en tant que service CDN pour cela ?

## **Réponse**

Non, vous ne le faites pas. Dans ce cas, vous pouvez ignorer l’utilisation de Fastly, au moins, au début du développement.

La seule situation que vous pouvez ne pas activer est pour un déploiement sans tête.
Voir [Cloud pour Adobe Commerce > Fastly](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html) dans notre documentation destinée aux développeurs.

Néanmoins, vous aurez probablement besoin de Fastly pour utiliser son certificat SSL.

Tous les clients d’Adobe Commerce sur l’infrastructure cloud reçoivent un certificat SSL partagé de Fastly dans le cadre du plan d’abonnement au cloud. L’ajout de son propre certificat SSL à Fastly est une option payante séparée et plutôt chère. Nous vous recommandons donc vivement d’activer Fastly et, au moins, de le tester dans les environnements d’évaluation et de production avant de passer en ligne, même pour votre site web Adobe Commerce sans interface.

## Informations supplémentaires

* [Sites web sans tête : Quel est le Big Deal avec l&#39;architecture découplée ?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) par [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Fastly](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html) dans notre documentation destinée aux développeurs.
