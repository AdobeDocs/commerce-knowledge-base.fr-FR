---
title: Informations d’expiration de certificat SSL personnalisées
description: Cet article fournit une solution pour lorsqu’un certificat SSL personnalisé a été mis à jour avec un certificat SSL fourni par un Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Informations d’expiration de certificat SSL personnalisées

Cet article fournit une solution pour lorsqu’un certificat SSL personnalisé a été mis à jour avec un certificat SSL fourni par un Adobe.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Adobe Commerce met automatiquement à jour les certificats SSL 30 jours avant l’expiration. Cette automatisation ne vérifie pas si le certificat remplacé est un SSL interne ou un SSL tiers personnalisé et le remplace par un SSL interne valide lors de la détection de l’expiration. Cela peut prêter à confusion pour les propriétaires et les opérateurs du site qui s’attendent à recevoir le certificat personnalisé sur le site, ainsi que le risque d’autres problèmes de fonctionnalités, notamment, mais sans s’y limiter, une panne du site.

<u>Étapes à reproduire</u>

1. Certificat SSL personnalisé installé pour le site web.
1. L’automatisation détecte que le certificat SSL personnalisé est à 30 jours de l’expiration.
1. Adobe Commerce remplace automatiquement le certificat personnalisé par notre certificat interne.

<u>Résultats attendus</u>

Adobe Commerce ignore les certificats personnalisés lors de l’exécution de sa mise à jour automatique de certificat SSL.

<u>Résultats réels</u>

Adobe Commerce met à jour tout certificat lorsqu’il est à 30 jours de l’expiration.

## Solution

Lorsqu’un commerçant choisit d’utiliser son propre certificat SSL personnalisé, il doit être mis à jour plus de 30 jours avant l’expiration du certificat pour s’assurer qu’il ne sera pas remplacé par un certificat SSL Adobe Commerce interne.

Si vous êtes dans une situation où votre SSL personnalisé a été remplacé par notre SSL interne et que vous souhaitez le remplacer par votre certificat SSL personnalisé mis à jour, veuillez [envoyer une demande d’assistance ;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) avec l’emplacement où vous avez chargé vos nouveaux fichiers de certificat. Veuillez inclure la date de début du nouveau SSL. Une fois que nous avons ces informations, nous pouvons passer à l’installation du nouveau certificat SSL.

## Lecture connexe

* [Certificats SSL (TLS) pour Magento Commerce Cloud : FAQ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) dans notre base de connaissances de soutien.
* [Référence des outils de ligne de commande : certification magento-cloud:add](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-cloud.html#certificateadd) dans notre documentation destinée aux développeurs.
* [Liste de contrôle de lancement](https://devdocs.magento.com/cloud/live/site-launch-checklist.html)dans notre documentation destinée aux développeurs.
* [Accès à l’outil d’analyse à l’échelle du site](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html#step-2-access-site-wide-analysis-tool) dans notre guide d’utilisation.
