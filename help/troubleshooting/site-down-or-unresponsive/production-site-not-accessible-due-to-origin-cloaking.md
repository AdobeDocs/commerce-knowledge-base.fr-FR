---
title: Site non accessible en raison du cloaking de l'origine
description: Cet article fournit une solution pour le cas où votre Adobe Commerce sur le storefront ou l’administrateur du site d’évaluation ou de production de l’infrastructure cloud n’est pas accessible.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Site non accessible en raison du cloaking de l&#39;origine

Cet article fournit une solution pour le cas où votre Adobe Commerce sur le storefront ou l’administrateur du site d’évaluation ou de production de l’infrastructure cloud n’est pas accessible.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud 2.3.x, 2.4.x

## Problème

https:&#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ n’est plus accessible.

<u>Procédure à suivre :</u>

1. Connectez-vous à votre projet.
1. Cliquez sur **Accéder au projet** pour obtenir la liste des URL et des SSH.

<u>Résultats réels:</u>

Le chargement de la page échoue avec l’erreur suivante :

*NET::ERR\_CERT\_INVALID* *alerte TLS, certificat incorrect (554) :*

<u>Résultats attendus :</u>

La page se charge correctement.

## Cause

Le cloaking d’origine a été activé, de sorte que l’origine n’est plus accessible directement.

Le cloaking d&#39;origine est une fonctionnalité de sécurité qui permet à Adobe Commerce de bloquer tout trafic non Fastly allant vers l&#39;infrastructure cloud (origine) afin d&#39;empêcher les attaques DDoS.

## Solution

* Si votre site cloud est actif, passez à https://mydomain.com/.
* Si vous disposez d’un site actif (non cloud), configurez un `mcprod.mydomain.com` de sous-domaine à l’aide du domaine https://mydomain.com/ et mettez à jour votre **URL de base** en *https://mcprod.mydomain.com*, puis [pointez le DNS vers Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#update-dns-configuration-with-development-settings).

## Lecture connexe

* [FAQ sur l&#39;activation du cloaking d&#39;origine Fastly](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) dans notre base de connaissances
* [Liste de contrôle pour la configuration d’un nouveau domaine](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain) dans notre base de connaissances d’assistance
