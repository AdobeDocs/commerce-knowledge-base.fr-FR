---
title: Bloquer le trafic malveillant pour Adobe Commerce à un niveau rapide
description: Cet article décrit les étapes à suivre pour bloquer le trafic malveillant lorsque vous pensez que votre Adobe Commerce sur le magasin d’infrastructures cloud est en train de subir une attaque DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
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

Pour accéder à l’administrateur, mettez votre site web en mode de maintenance comme décrit dans la section [Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) et whitelister votre adresse IP. Désactivez le mode de maintenance une fois cette opération terminée.

## Bloquer le trafic par IP

Pour Adobe Commerce sur le magasin d’infrastructure cloud, le moyen le plus efficace de bloquer le trafic par des adresses IP et des sous-réseaux spécifiques consiste à ajouter une liste de contrôle d’accès pour Fastly dans l’administrateur de Commerce. Vous trouverez ci-dessous les étapes comportant des liens vers des instructions plus détaillées :

1. Dans l’administrateur de Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète** > **Configuration rapide**.
1. [Création d’une ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) avec une liste d&#39;adresses IP ou de sous-réseaux que vous allez bloquer.
1. Ajoutez-le à la liste ACL et bloquez-le, comme décrit dans la section [Blocage](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) Guide du module Fastly\_Cdn pour Adobe Commerce.

## Bloquer le trafic par pays

Pour Adobe Commerce sur la boutique d’infrastructures cloud, le moyen le plus efficace de bloquer le trafic par pays est d’ajouter une liste de contrôle d’accès pour Fastly dans l’administrateur Commerce.

1. Dans l’administrateur de Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète** > **Configuration rapide**.
1. Sélectionnez les pays et configurez le blocage à l’aide de l’ACL, comme décrit dans la section [Blocage](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) Guide du module Fastly\_Cdn pour Adobe Commerce.

## Blocage du trafic par l’agent utilisateur

Pour établir un blocage basé sur l’agent utilisateur, vous devez ajouter un extrait de code VCL personnalisé à votre configuration Fastly. Pour ce faire, procédez comme suit :

1. Dans l’administrateur de Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète**.
1. Alors **Configuration rapide** > **Fragments de code VCL personnalisés**.
1. Créez un fragment de code personnalisé comme décrit dans la section [Fragments de code VCL personnalisés](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) Guide du module Fastly\_Cdn. Vous pouvez utiliser l’exemple de code suivant à titre d’exemple. Cet exemple désactive le trafic pour la variable `AhrefsBot` et `SemrushBot` agents utilisateurs.

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

Il existe une fonctionnalité expérimentale Fastly pour Adobe Commerce sur l’infrastructure cloud qui vous permet de spécifier la limite de taux pour des chemins et des robots d’indexation particuliers. Veuillez consulter la section [Documentation du module Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) pour plus d’informations.

Les fonctionnalités doivent être largement testées lors de l’évaluation, avant d’être utilisées en production, car elles peuvent bloquer le trafic légitime.

## Recommandé : pensez à mettre à jour robots.txt

Mettre à jour votre `robots.txt` peut contribuer à empêcher certains moteurs de recherche, robots et robots d’analyser certaines pages. Les pages qui ne doivent pas être analysées sont les pages de résultats de recherche, le passage en caisse, les informations sur les clients, etc. Empêcher les robots d&#39;analyser ces pages pourrait contribuer à réduire le nombre de requêtes générées par ces robots.

Il existe deux considérations importantes lors de l’utilisation de `robots.txt`:

* Les robots peuvent ignorer votre `robots.txt`. En particulier les robots malveillants qui analysent le web à la recherche de failles de sécurité, et les collecteurs d&#39;adresses email utilisés par les spammeurs ne prêteront aucune attention.
* La variable `robots.txt` est un fichier disponible publiquement. N&#39;importe qui peut voir quelles sections de votre serveur vous ne voulez pas que les robots utilisent.

Informations de base et Adobe Commerce par défaut `robots.txt` se trouve dans la section [Robots des moteurs de recherche](https://docs.magento.com/m2/ee/user_guide/marketing/search-engine-robots.html) dans notre documentation destinée aux développeurs.

Pour obtenir des informations générales et des recommandations sur `robots.txt`, voir :

* [Créer un fichier robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) fichier du support Google
* [A propos de /robots.txt](https://www.robotstxt.org/robotstxt.html) par robotstxt.org

Collaborez avec votre développeur et/ou votre expert SEO pour déterminer les agents utilisateur que vous souhaitez autoriser ou ceux que vous souhaitez interdire.

## Lecture connexe

[Conditions de licence spécifiques aux produits pour Adobe Commerce sur le cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
