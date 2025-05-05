---
title: Bloquer le trafic malveillant pour Adobe Commerce au niveau Fastly
description: Cet article décrit les mesures que vous pouvez prendre pour bloquer le trafic malveillant lorsque vous suspectez que votre Adobe Commerce sur le magasin d’infrastructure cloud subit une attaque DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Bloquer le trafic malveillant pour Adobe Commerce au niveau Fastly

Cet article décrit les mesures que vous pouvez prendre pour bloquer le trafic malveillant lorsque vous suspectez que votre Adobe Commerce sur le magasin d’infrastructure cloud subit une attaque DDoS.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.3.x

Dans cet article, nous supposons que vous disposez déjà des adresses IP malveillantes et/ou de leur pays et des agents utilisateurs. Les utilisateurs d’Adobe Commerce sur les infrastructures cloud obtiennent généralement ces informations de l’assistance d’Adobe Commerce. Les sections suivantes décrivent les étapes à suivre pour bloquer le trafic en fonction de ces informations. Toutes les modifications doivent être effectuées dans l’environnement de production.

## Obtenir l’accès au panneau d’administration

Si votre site web est surchargé par DDoS, il se peut que vous ne puissiez pas vous connecter à votre administrateur Commerce (et effectuer toutes les étapes décrites plus en détail dans cet article).

Pour accéder à l’administrateur, mettez votre site web en mode de maintenance comme décrit dans la section [ Activer ou désactiver le mode de maintenance ](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) et placez votre adresse IP sur liste blanche. Désactivez le mode de maintenance une fois cette opération terminée.

## Bloquer le trafic par adresse IP

Pour le magasin d’infrastructure cloud d’Adobe Commerce, le moyen le plus efficace de bloquer le trafic par des adresses IP et des sous-réseaux spécifiques est d’ajouter une liste de contrôle d’accès pour Fastly dans l’administrateur Commerce. Vous trouverez ci-dessous les étapes avec des liens vers des instructions plus détaillées :

1. Dans l’Administration Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complet** > **Fastly Configuration**.
1. [Créez une liste de contrôle d’accès](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) avec une liste d’adresses IP ou de sous-réseaux que vous allez bloquer.
1. Ajoutez-le à la liste ACL et bloquez-le comme décrit dans le guide [Blocage](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) pour le module Fastly\_Cdn pour Adobe Commerce.

## Bloquer le trafic par pays

Pour le magasin d’infrastructure cloud d’Adobe Commerce, la méthode la plus efficace pour bloquer le trafic par pays consiste à ajouter une liste de contrôle d’accès pour Fastly dans l’administrateur Commerce.

1. Dans l’Administration Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complet** > **Fastly Configuration**.
1. Sélectionnez les pays et configurez le blocage à l’aide de l’ACL comme décrit dans le guide [Blocage](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) pour le module Fastly\_Cdn pour Adobe Commerce.

## Bloquer le trafic par l’agent utilisateur

Pour établir un blocage basé sur l’agent utilisateur, vous devez ajouter un fragment de code VCL personnalisé à votre configuration Fastly. Pour ce faire, procédez comme suit :

1. Dans Commerce Admin, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complet**.
1. Puis **Configuration rapide** > **Fragments de code VCL personnalisés**.
1. Créez le nouveau fragment de code personnalisé comme décrit dans le guide [Fragments de code VCL personnalisés](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) pour le module Fastly_Cdn. Vous pouvez utiliser l’exemple de code suivant comme exemple. Cet exemple montre comment interdire le trafic pour les agents utilisateurs `AhrefsBot` et `SemrushBot`.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Limitation de débit (fonctionnalité expérimentale Fastly)

Il existe une fonctionnalité Fastly expérimentale pour Adobe Commerce sur les infrastructures cloud qui vous permet de spécifier la limite de débit pour des chemins et des robots d’exploration spécifiques. Veuillez consulter la [documentation du module Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) pour plus d’informations.

Cette fonctionnalité doit être testée de manière approfondie lors de l’évaluation, avant d’être utilisée en production, car elle peut bloquer le trafic légitime.

## Recommandé : envisagez de mettre à jour robots.txt

La mise à jour de votre fichier `robots.txt` peut aider à empêcher certains moteurs de recherche, robots et robots d’analyser certaines pages. Parmi les exemples de pages qui ne doivent pas être explorées, citons les pages de résultats de recherche, le passage en caisse, les informations client, etc. Empêcher les robots d&#39;analyser ces pages pourrait aider à réduire le nombre de requêtes générées par ces robots.

Deux points importants doivent être pris en compte lors de l’utilisation de `robots.txt` :

* Les robots peuvent ignorer vos `robots.txt`. Surtout les robots malveillants, qui analysent le Web à la recherche de failles de sécurité, et les collecteurs d&#39;adresses électroniques utilisés par les spammeurs ne prêteront aucune attention.
* Le fichier `robots.txt` est un fichier accessible au public. Tout le monde peut voir les sections de votre serveur que vous ne voulez pas que les robots utilisent.

Vous trouverez les informations de base et la configuration par défaut du `robots.txt` Adobe Commerce dans l’article [Robots de moteurs de recherche](https://experienceleague.adobe.com/fr/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) de notre documentation destinée aux développeurs et développeuses.

Pour obtenir des informations générales et des recommandations sur les `robots.txt`, voir :

* [Création d’un fichier robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) par le support Google
* [À propos de /robots.txt](https://www.robotstxt.org/robotstxt.html) par robotstxt.org

Contactez votre développeur et/ou un expert en SEO pour déterminer les agents utilisateur que vous souhaitez autoriser ou non.

## Lecture connexe

* [Termes de licence spécifiques au produit pour Adobe Commerce on Cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
* [VCL personnalisé pour le blocage des requêtes](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking) dans le guide Commerce sur le cloud
