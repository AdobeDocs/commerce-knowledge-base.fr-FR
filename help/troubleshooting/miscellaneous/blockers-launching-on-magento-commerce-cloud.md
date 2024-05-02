---
title: Blocages lancés sur Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit un correctif permettant aux bloqueurs de se lancer sur Adobe Commerce sur l’infrastructure cloud, y compris les problèmes liés à la configuration Fastly, aux certificats SSL, aux redirections 301 et aux performances des ressources statiques.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: 3dd44b72bc9f02fe808b70355c4331fc28aa3606
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Blocages lancés sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit un correctif permettant aux bloqueurs de se lancer sur Adobe Commerce sur l’infrastructure cloud, y compris les problèmes liés à la configuration Fastly, aux certificats SSL, aux redirections 301 et aux performances des ressources statiques.

## 1. Configuration rapide

[Fastly](https://www.fastly.com/) est un réseau de diffusion de contenu (CDN) de type vernis destiné à diffuser des ressources statiques. Elle est requise pour Adobe Commerce sur l’infrastructure cloud dans les environnements de production. Il est donc important de configurer Fastly et de tester votre site web (UAT) avec Activé et Configuré Fastly, à la fois dans les environnements d’évaluation et de production.

>[!WARNING]
>
>Lorsque le FPC (Full Page Cache) est activé, votre site web fonctionne différemment. Assurez-vous de le tester avant de passer en ligne.

Le processus de configuration Fastly est décrit en détail dans la section [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans notre guide d’utilisation. Vous trouverez ci-dessous les étapes importantes.

### 1a. Assurez-vous que la version la plus récente du module Fastly est installée

Assurez-vous que la version la plus récente du module Fastly est installée pour bénéficier des dernières fonctionnalités et améliorations. Pour vérifier si vous disposez de la dernière version de Fastly, consultez [Mettre à niveau le module Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) dans notre guide d’utilisation. Pour plus d’informations, voir [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans notre guide d’utilisation.

### 1b. Activation et configuration rapide à l’aide de l’administrateur Commerce

Pour plus d’informations, voir [Obtention de vos informations d’identification rapides](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) dans notre guide d’utilisation.

### 1c. Chargement rapide de fragments de code VCL

Pour plus d’informations, voir [Chargement rapide de VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans notre guide d’utilisation.

Vous pouvez également [créer et ajouter des fragments de code VCL personnalisés ;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html).

### 1j. Configuration de DNS pour Fastly


Reportez-vous à cet article pour obtenir les étapes détaillées : [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) dans notre guide d’utilisation.

### Articles associés Fastly dans notre base de connaissances d&#39;assistance

* [La mise en cache rapide ne fonctionne pas sur Cloud](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [Erreur lors de la purge du cache Fastly dans Cloud (la requête de purge n’a pas été traitée correctement)](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2. Certificat SSL (TLS) valide

Problème : en l’absence d’un certificat SSL valide et fonctionnel, vous ne pouvez pas tester les méthodes de paiement externes sur la page Passage en caisse - dans l’environnement d’évaluation.

Recommandation **:** Demandez votre certificat SSL partagé pour les noms de domaine intermédiaire ou actif.

Découvrez les certificats SSL dans cette section [FAQ rapide](/help/announcements/adobe-commerce-announcements/magento-ssl-tls-certificate-requirements-and-clean-up.md) article de notre base de connaissances en matière de soutien.

## 3. Configuration et test des redirections 301

Problème : les redirections 301 ne sont pas fournies ou mal configurées, ce qui entraîne la chute de votre magasin dans les classements SEO et les listes de recherche.

Recommandation **:** Configurez et testez soigneusement les redirections 301.

Si vous migrez d’un ancien site web vers un nouveau, les redirections 301 amènent vos clients des anciennes pages indexées précédemment vers les pages appropriées de votre nouveau magasin, comme ceci :

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Articles connexes :**

* [Redirections à travers routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html) dans notre guide d’utilisation.
* [Redirections via la console Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) dans notre guide d’utilisation.
* [URL Rewrites](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html) dans notre guide d’utilisation.

## 4. Performances des ressources

Problème : les ressources statiques sont diffusées lentement, de sorte que les performances de votre site sont faibles (temps de chargement long, contenu multimédia non affiché, etc.). Les ressources statiques de votre site web sont des ressources CSS, des images, des vidéos, des documents joints, etc. La manière dont ils sont organisés et servis est un facteur clé des performances de votre site.

Recommandation : pour identifier les causes possibles des performances médiocres, utilisez [Kit d’outils de performances Adobe Commerce](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) pour les tests de performances. Vous pouvez également tenir compte des outils tiers suivants :

* [Siège](https://www.joedog.org/siege-home/): utilitaire de test de chargement et d’évaluation des performances HTTP ; prend en charge l’authentification de base, les cookies, les protocoles HTTP, HTTPS et FTP.
* [Jeter](https://jmeter.apache.org/): un outil fiable de test de charge et de mesure des performances. Permet d’évaluer les performances du trafic en pointe, par exemple pour les ventes Flash.
* [New Relic](https://support.newrelic.com/): localise les processus et les zones du site, ce qui entraîne des performances ralenties avec le temps passé par action suivi, comme la transmission de données, de requêtes, de redis, etc.
* [WebPageTest](https://www.webpagetest.org/) (gratuit) et [Pingdom](https://www.pingdom.com/) (payant) : analyse en temps réel des pages de votre site en temps réel avec différents emplacements d’origine.

Vous pouvez également envisager [minimisation](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) pour CSS, JavaScript et HTML.

**Articles connexes :**

* [Test du déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html) dans notre documentation destinée aux développeurs.
