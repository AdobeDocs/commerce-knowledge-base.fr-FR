---
title: Bloqueurs lancés sur Adobe Commerce sur les infrastructures cloud
description: Cet article fournit un correctif pour les bloqueurs à lancer sur Adobe Commerce sur les infrastructures cloud, y compris les problèmes liés à la configuration Fastly, aux certificats SSL, aux redirections 301 et aux performances des ressources statiques.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: d653957b94127e8b1d37a66c069a618f34ac5af9
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Bloqueurs lancés sur Adobe Commerce sur les infrastructures cloud

Cet article fournit un correctif pour les bloqueurs à lancer sur Adobe Commerce sur les infrastructures cloud, y compris les problèmes liés à la configuration Fastly, aux certificats SSL, aux redirections 301 et aux performances des ressources statiques.

## &#x200B;1. Configuration rapide

[Fastly](https://www.fastly.com/) est un réseau de diffusion de contenu (CDN) basé sur Varnish qui sert des ressources statiques. Cela est nécessaire pour Adobe Commerce sur les infrastructures cloud dans les environnements de production. Il est donc important de configurer Fastly et de tester votre site web (UAT) avec Fastly activé et configuré, dans les environnements d’évaluation et de production.

>[!WARNING]
>
>Lorsque le cache de page complète (FPC) est activé, les performances de votre site web sont différentes. Veillez à le tester avant de le publier.

Le processus de configuration de Fastly est documenté en détail dans la rubrique [Configuration de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) de notre guide de l’utilisateur. Vous trouverez ci-dessous les étapes importantes.

### 1 bis. Assurez-vous que la version la plus récente du module Fastly est installée

Assurez-vous que vous disposez de la version la plus récente du module Fastly installé pour obtenir les dernières fonctionnalités et améliorations. Pour vérifier si vous disposez de la dernière version de Fastly, consultez [Mise à niveau du module Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#upgrade-the-fastly-module) dans notre guide de l’utilisateur. Pour plus d’informations, consultez [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) dans notre guide de l’utilisateur.

### 1 ter. Activer et configurer Fastly à l’aide de l’administrateur Commerce

Pour plus d’informations, consultez [Obtention de vos informations d’identification Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#get-fastly-credentials) dans notre guide de l’utilisateur.

### 1 quater. Chargement rapide de fragments de code VCL

Pour plus d’informations, voir [Télécharger VCL sur Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) dans notre guide de l’utilisateur.

Vous pouvez également [créer et ajouter vos propres fragments de code VCL personnalisés](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=fr).

### 1d. Configuration du DNS pour Fastly


Reportez-vous à cet article pour les étapes détaillées : [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#update-dns-configuration-with-development-settings) dans notre guide d’utilisation.

## &#x200B;2. Certificat SSL (TLS) valide

Problème : Sans certificat SSL valide et fonctionnel, vous ne pouvez pas tester les méthodes de paiement externes sur la page Passage en caisse, dans l’environnement d’évaluation.

Recommandation **:** demandez votre certificat SSL partagé pour les noms de domaine Staging ou Live.


## &#x200B;3. Configuration et test des redirections 301

Problème : les redirections 301 ne sont pas fournies ou sont mal configurées, ce qui entraîne une baisse de votre magasin dans les classements SEO et les listes de recherche.

Recommandation **:** configurer et tester soigneusement les redirections 301.

Si vous migrez d’un ancien site web vers un nouveau, le 301 redirige vos clients des anciennes pages précédemment indexées vers les pages appropriées de votre nouvelle boutique, comme suit :

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Articles connexes :**

* [Redirige via routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=fr) dans notre guide de l&#39;utilisateur.
* [Redirige via Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr) dans notre guide d’utilisation.
* [Réécritures d’URL](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=fr) dans notre guide d’utilisation.

## &#x200B;4. Performances des ressources

Problème : les ressources statiques sont diffusées lentement afin que votre site présente de faibles performances (temps de chargement long, contenu multimédia non affiché, etc.). Les ressources statiques de votre site web sont les ressources CSS, les images, les vidéos, les documents joints, etc. La manière dont ils sont organisés et diffusés est un facteur clé dans la performance de votre site.

Recommandation : pour identifier les causes possibles de mauvaises performances, pensez à utiliser [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) pour les tests de performance. Vous pouvez également tenir compte des outils tiers suivants :

* [Siege](https://www.joedog.org/siege) : utilitaire de test de chargement et d’évaluation des performances HTTP ; prend en charge l’authentification de base, les cookies, les protocoles HTTP, HTTPS et FTP.
* [Jmeter](https://jmeter.apache.org/) : outil de test de charge et de mesure des performances réputé. Permet d’évaluer les performances pour le trafic en pic, par exemple pour les ventes flash.
* [New Relic](https://support.newrelic.com/) : localise les processus et les zones du site, ce qui ralentit les performances en raison du temps passé par action suivi, comme la transmission de données, de requêtes, de Redis, etc.
* [WebPageTest](https://www.webpagetest.org/) (gratuit) et [Pingdom](https://www.pingdom.com/) (payant) : l’analyse en temps réel des pages de votre site charge du temps avec différents emplacements d’origine.

Vous pouvez également envisager une [minification](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=fr) pour CSS, JavaScript et HTML.

**Articles connexes :**

* [Tester le déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=fr) dans notre documentation destinée aux développeurs.
