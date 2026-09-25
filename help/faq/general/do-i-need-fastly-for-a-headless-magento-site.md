---
title: Ai-je besoin de Fastly pour un site Adobe Commerce découplé ?
description: Ai-je besoin de Fastly pour un site Adobe Commerce découplé ?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%
---
# Ai-je besoin de Fastly pour un site Adobe Commerce découplé ?

>[!NOTE]
>
>Tous les clients doivent utiliser Fastly pour leurs environnements de production et d’évaluation. Fastly est un réseau de diffusion de contenu (CDN) qui fournit une mise en cache complète des pages, une optimisation des images et des services de sécurité (DDoS et WAF) dans le cadre de vos projets d’infrastructure cloud Adobe Commerce. Il s’agit des composants principaux de la solution Adobe Commerce, qui offrent des performances et une sécurité accrues. Ces fonctionnalités font partie de la conformité PCI Adobe. Vous devez configurer ces services Fastly sur vos environnements de Principal de démarrage, d’évaluation, d’évaluation pro et de production. Si vous utilisez Adobe Commerce dans un déploiement découplé, tout le trafic d’API provenant de l’Internet public doit passer par Fastly et nous vous recommandons vivement d’utiliser Fastly pour mettre en cache les réponses de GraphQL. Consultez le [Guide du développeur de GraphQL > Mise en cache avec Fastly &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly) dans notre documentation destinée aux développeurs.

## **Question**

Je développe une implémentation découplée d’Adobe Commerce. Dois-je toujours utiliser Fastly en tant que service de réseau CDN ?

## **Réponse**

Non, pas du tout. Dans cette situation, vous pouvez ignorer l’utilisation de Fastly, du moins au début du développement.

La seule situation que vous ne souhaitez peut-être pas activer concerne un déploiement découplé.
Consultez [Cloud for Adobe Commerce > Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly) dans notre documentation destinée aux développeurs.

Néanmoins, vous aurez très probablement besoin de Fastly pour utiliser son certificat SSL.

Tous les clients Adobe Commerce sur les infrastructures cloud reçoivent un certificat SSL partagé de Fastly dans le cadre du plan d’abonnement au cloud. L’ajout de son propre certificat SSL à Fastly est une option payante distincte et assez coûteuse. Nous vous recommandons donc vivement d’activer Fastly et de le tester au moins dans les environnements d’évaluation et de production avant sa mise en ligne, même pour votre site web Adobe Commerce découplé.

## Plus d’informations

* [Sites web découplés : quel est le problème avec l’architecture découplée ?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) par [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly) dans notre documentation destinée aux développeurs et développeuses.
