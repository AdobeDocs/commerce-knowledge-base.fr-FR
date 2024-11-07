---
title: Bloquer le trafic malveillant pour Adobe Commerce à un niveau rapide
description: Cet article décrit les étapes à suivre pour bloquer le trafic malveillant lorsque vous pensez que votre Adobe Commerce sur le magasin d’infrastructures cloud est en train de subir une attaque DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Bloquer le trafic malveillant pour Adobe Commerce à un niveau rapide

Cet article décrit les étapes à suivre pour bloquer le trafic malveillant lorsque vous pensez que votre Adobe Commerce sur le magasin d’infrastructures cloud est en train de subir une attaque DDoS.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud 2.3.x

Dans cet article, nous supposons que vous disposez déjà des adresses IP malveillantes et/ou de leur pays et agents utilisateurs. Les utilisateurs d’Adobe Commerce sur l’infrastructure cloud obtiennent généralement ces informations auprès de l’assistance d’Adobe Commerce. Les sections suivantes décrivent les étapes de blocage du trafic en fonction de ces informations. Toutes les modifications doivent être effectuées dans l’environnement Production.

## Accès au panneau d’administration

Si votre site web est surchargé par DDoS, vous ne pourrez peut-être pas vous connecter à votre administrateur Commerce (et effectuer toutes les étapes décrites plus loin dans cet article).

Pour accéder à l’administrateur, mettez votre site web en mode de maintenance comme décrit dans [Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) et whitelistez votre adresse IP. Désactivez le mode de maintenance une fois cette opération terminée.

## Bloquer le trafic par IP

Pour Adobe Commerce sur le magasin d’infrastructure cloud, le moyen le plus efficace de bloquer le trafic par des adresses IP et des sous-réseaux spécifiques consiste à ajouter une liste de contrôle d’accès pour Fastly dans l’administrateur de Commerce. Vous trouverez ci-dessous les étapes comportant des liens vers des instructions plus détaillées :

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète** > **Configuration rapide**.
1. [Créez une ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) avec une liste d’adresses IP ou de sous-réseaux que vous allez bloquer.
1. Ajoutez-le à la liste ACL et bloquez-le, comme décrit dans le guide [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) correspondant au module Fastly\_Cdn pour Adobe Commerce.

## Bloquer le trafic par pays

Pour Adobe Commerce sur la boutique d’infrastructures cloud, le moyen le plus efficace de bloquer le trafic par pays est d’ajouter une liste de contrôle d’accès pour Fastly dans l’administrateur Commerce.

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète** > **Configuration rapide**.
1. Sélectionnez les pays et configurez le blocage à l’aide de l’ACL, comme décrit dans le guide [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) du module Fastly\_Cdn pour Adobe Commerce.

## Blocage du trafic par l’agent utilisateur

Pour établir un blocage basé sur l’agent utilisateur, vous devez ajouter un extrait de code VCL personnalisé à votre configuration Fastly. Pour ce faire, procédez comme suit :

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète**.
1. Ensuite, **Configuration Fastly** > **Fragments de code VCL personnalisés**.
1. Créez le nouveau fragment de code personnalisé comme décrit dans le guide [Fragments de code VCL personnalisés](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) pour le module Fastly\_Cdn. Vous pouvez utiliser l’exemple de code suivant à titre d’exemple. Cet exemple désactive le trafic pour les agents utilisateurs `AhrefsBot` et `SemrushBot`.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Limitation de taux (fonctionnalité expérimentale Fastly)

Il existe une fonctionnalité expérimentale Fastly pour Adobe Commerce sur l’infrastructure cloud qui vous permet de spécifier la limite de taux pour des chemins et des robots d’indexation particuliers. Pour plus d’informations, reportez-vous à la [documentation du module Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) .

Les fonctionnalités doivent être largement testées lors de l’évaluation, avant d’être utilisées en production, car elles peuvent bloquer le trafic légitime.

## Recommandé : pensez à mettre à jour robots.txt

La mise à jour de votre fichier `robots.txt` peut vous aider à empêcher certains moteurs de recherche, robots et robots d’analyser certaines pages. Les pages qui ne doivent pas être analysées sont les pages de résultats de recherche, le passage en caisse, les informations sur les clients, etc. Empêcher les robots d&#39;analyser ces pages pourrait contribuer à réduire le nombre de requêtes générées par ces robots.

Il y a deux points importants à prendre en compte lors de l’utilisation de `robots.txt` :

* Les robots peuvent ignorer votre `robots.txt`. En particulier les robots malveillants qui analysent le web à la recherche de failles de sécurité, et les collecteurs d&#39;adresses email utilisés par les spammeurs ne prêteront aucune attention.
* Le fichier `robots.txt` est un fichier disponible publiquement. N&#39;importe qui peut voir quelles sections de votre serveur vous ne voulez pas que les robots utilisent.

Les informations de base et la configuration Adobe Commerce `robots.txt` par défaut sont disponibles dans l’article [Robots de moteur de recherche](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) de notre documentation destinée aux développeurs.

Pour obtenir des informations générales et des recommandations sur `robots.txt`, voir :

* [Création d’un fichier robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) par le support Google
* [À propos de /robots.txt](https://www.robotstxt.org/robotstxt.html) par robotstxt.org

Collaborez avec votre développeur et/ou votre expert SEO pour déterminer les agents utilisateur que vous souhaitez autoriser ou ceux que vous souhaitez interdire.

## Lecture connexe

[Conditions de licence spécifiques à un produit pour Adobe Commerce sur Cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
