---
title: Test rapide en exploitation si un site actif utilise le même domaine
description: Si un site actif est opérationnel sur votre domaine de production (« exemple.com ») et que vous devez tester votre nouveau magasin sur Adobe Commerce dans l’environnement de production de l’infrastructure cloud avec le réseau CDN Fastly activé, nous vous recommandons d’utiliser le sous-domaine (tel que « prod.exemple.com »), l’ayant précédemment ajouté à Fastly, pour toute activité de test préalable au lancement. Cet article en détaille les détails et fournit des liens utiles vers les ressources de documentation Adobe Commerce associées.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Test rapide en exploitation si un site actif utilise le même domaine

Si un site actif est opérationnel sur votre domaine de production (`example.com`) et que vous devez tester votre nouveau magasin sur Adobe Commerce dans l’environnement de production de l’infrastructure cloud avec le réseau CDN Fastly activé, nous vous recommandons d’utiliser le sous-domaine (tel que `prod.example.com`), l’avoir précédemment ajouté à Fastly, pour toute activité de test préalable au lancement. Cet article en détaille les détails et fournit des liens utiles vers les ressources de documentation Adobe Commerce associées.

## Problème

Votre boutique actuelle qui utilise le domaine de production `example.com` est en ligne et en cours d’exploitation. Cependant, vous devez tester votre nouveau magasin, créé avec Adobe Commerce sur une infrastructure cloud et déployé dans l’environnement de production, avec le service de cache de pages complètes Fastly activé.

Le problème est que l’environnement de production de votre projet d’infrastructure cloud d’Adobe Commerce utilise le même domaine actif (`example.com`) et que vous ne pouvez pas faire basculer votre nouveau site vers ce domaine, en laissant simultanément votre Live Store en cours d’exécution sur le même domaine.

### Pourquoi utiliser Fastly à des fins de test dans l’environnement de production ?

En théorie, vous pouvez ignorer l’utilisation du réseau CDN Fastly et tester votre Adobe Commerce sur le magasin d’infrastructure cloud dans l’environnement de production sans activer le cache de page entière.

Cependant, avec le cache de pleine page activé, les performances de votre boutique sont différentes ; vous ne connaissez jamais les performances réelles de votre site en direct si vous ne l’avez pas testé avec le réseau CDN avant de le lancer. Tester votre boutique en production avec le réseau CDN Fastly activé est la recommandation officielle d’Adobe Commerce.

## Solution : utilisez le sous-domaine de production

Utilisez le sous-domaine de premier niveau (`prod.example.com`) pour votre nouveau magasin Adobe Commerce sur l’infrastructure cloud dans l’environnement de production, tout en conservant le site actif actuel sur le domaine de base (`example.com`).

Lors de la planification de votre projet Adobe Commerce sur l’infrastructure cloud, vous pouvez spécifier un tel sous-domaine de production et demander à l’équipe de l’infrastructure cloud de pointer le sous-domaine vers le service Fastly.

Pour traiter le sous-domaine dans votre projet d’infrastructure cloud Adobe Commerce, procédez comme suit :

* [Envoyez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) en demandant d’ajouter le sous-domaine à la configuration du service Fastly/Nginx (pour l’architecture de plan Pro de l’infrastructure cloud d’Adobe Commerce).
* Configurez les paramètres DNS correspondants de votre côté.

Après avoir suivi les étapes de configuration du sous-domaine, vous devez également suivre les étapes suivantes pour valider votre domaine de production pour le certificat SSL :

* Chargez l’enregistrement TXT du DNS pour la validation SSL de votre domaine de production.
* [Envoyez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) demandant de valider le domaine de production pour le certificat SSL.

L’utilisation du sous-domaine vous permet d’effectuer un « lancement logiciel » de votre magasin à l’avenir, car ce lancement nécessite uniquement la mise à jour des paramètres DNS correspondants.

## Documentation connexe

Dans notre base de connaissances du support :

* [Configurer les paramètres DNS Fastly sur les environnements d’évaluation et de production](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=fr)
* [Configuration du plan Fastly for Starter sur le cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html?lang=fr)
* [Bloqueurs potentiels à lancer sur Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=fr)

Dans notre documentation destinée aux développeurs :

* [Aperçu rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=fr)
* [Liste de contrôle de mise en production : configurations DNS pour Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=fr)
