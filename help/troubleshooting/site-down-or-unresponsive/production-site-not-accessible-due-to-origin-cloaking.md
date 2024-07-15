---
title: Site inaccessible en raison du cloaking d’origine
description: Cet article fournit une solution lorsque votre site d’évaluation de l’infrastructure cloud ou de production Adobe Commerce et/ou l’administrateur n’est pas accessible.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Site inaccessible en raison du cloaking d’origine

Cet article fournit une solution lorsque votre site d’évaluation de l’infrastructure cloud ou de production Adobe Commerce et/ou l’administrateur n’est pas accessible.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.x, 2.4.x

## Problème

https: &#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ n’est plus accessible.

<u>Étapes à reproduire :</u>

1. Connectez-vous à votre projet.
1. Cliquez sur **Accéder au projet** pour obtenir une liste d’URL et de SSH.

<u>Résultats réels :</u>

Échec du chargement de la page avec l’erreur suivante :

*NET::ERR\_CERT\_INVALID* *Alerte TLS, mauvais certificat (554) :*

<u>Résultats attendus :</u>

Chargement de la page réussi.

## Cause

Le cloaking d’origine a été activé, de sorte que l’origine n’est plus directement accessible.

Le cloaking d’origine est une fonctionnalité de sécurité qui permet à Adobe Commerce de bloquer tout trafic non-Fastly se rendant dans l’infrastructure cloud (origine) pour empêcher les attaques DDoS.

## Solution

* Si votre site cloud est actif, passez à https://mydomain.com/.
* Si vous disposez d’un site actif (non cloud), à l’aide du domaine https://mydomain.com/, configurez un sous-domaine `mcprod.mydomain.com` et remplacez par mettre à jour votre **URL de base** vers *https://mcprod.mydomain.com*, puis [pointez le DNS vers Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#update-dns-configuration-with-development-settings).

## Lecture connexe

[FAQ sur l’activation du cloaking d’origine Fastly](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) dans notre base de connaissances d’assistance.
