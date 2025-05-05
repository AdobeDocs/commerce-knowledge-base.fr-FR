---
title: Tester rapidement en production si un site actif utilise le même domaine
description: Si votre site en ligne est opérationnel sur votre domaine de production (&grave;exemple.com&grave;) et que vous devez tester votre nouvelle boutique dans Adobe Commerce sur l’environnement de production de l’infrastructure cloud avec un réseau de diffusion de contenu Fastly activé, nous vous recommandons d’utiliser le sous-domaine (comme "prod.exemple.com"), l’ayant précédemment ajouté à Fastly, pour toute activité de test de prélancement. Cet article présente les détails et fournit des liens utiles vers les ressources de documentation Adobe Commerce connexes.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Tester rapidement en production si un site actif utilise le même domaine

Si votre site en ligne est opérationnel sur votre domaine de production (`example.com`) et que vous devez tester votre nouvelle boutique sur Adobe Commerce dans l’environnement de production de l’infrastructure cloud avec un réseau de diffusion de contenu Fastly activé, nous vous recommandons d’utiliser le sous-domaine (comme `prod.example.com`), qui l’a précédemment ajouté à Fastly, pour toute activité de test de prélancement. Cet article présente les détails et fournit des liens utiles vers les ressources de documentation Adobe Commerce connexes.

## Problème

Votre magasin actuel qui utilise le domaine de production `example.com` est actif et opérationnel. Cependant, vous devez tester votre nouveau magasin, créé avec Adobe Commerce sur l’infrastructure cloud et déployé dans l’environnement de production, avec le service de cache de page complet et rapide activé.

Le problème est que l’environnement de production de votre projet d’infrastructure cloud Adobe Commerce utilise le même domaine en direct (`example.com`) et que vous ne pouvez pas passer votre nouveau site à ce domaine, en exécutant simultanément votre boutique en ligne actuelle sur le même domaine.

### Pourquoi utiliser Fastly pour tester l’environnement de production ?

En théorie, vous pouvez ignorer l’utilisation d’un réseau de diffusion de contenu Fastly et tester votre Adobe Commerce dans le magasin d’infrastructures cloud de l’environnement de production sans activation du cache de page complet.

Toutefois, avec le cache de page entière activé, votre magasin fonctionne différemment. Vous ne connaissez jamais les performances réelles en direct de votre site si vous ne l’avez pas testé avec le réseau de diffusion de contenu avant le lancement. Le test de votre magasin en production avec un réseau de diffusion de contenu Fastly activé est la recommandation officielle d’Adobe Commerce.

## Solution : utiliser le sous-domaine de production

Utilisez le sous-domaine de premier niveau (`prod.example.com`) pour votre nouvelle boutique Adobe Commerce sur l’infrastructure cloud de l’environnement de production tout en conservant le site actif sur le domaine de base (`example.com`).

Lors de la planification de votre projet d’infrastructure cloud Adobe Commerce, vous pouvez spécifier un sous-domaine de production de ce type et demander à l’équipe d’infrastructure cloud de pointer le sous-domaine vers le service Fastly.

Pour traiter le sous-domaine dans votre projet d’infrastructure cloud Adobe Commerce, procédez comme suit :

* [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant d’ajouter le sous-domaine à la configuration Fastly service/Nginx (pour l’architecture de plan Adobe Commerce on cloud infrastructure Pro).
* Configurez les paramètres DNS correspondants sur votre côté.

Après avoir exécuté les étapes de configuration de sous-domaine, vous devez également procéder comme suit pour valider votre domaine de production pour le certificat SSL :

* Téléchargez l’enregistrement TXT DNS pour la validation SSL de votre domaine de production.
* [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant la validation du domaine de production pour le certificat SSL.

L’utilisation du sous-domaine vous permet d’effectuer un &quot;lancement soft&quot; de votre magasin à l’avenir, car ce lancement nécessite uniquement la mise à jour des paramètres DNS correspondants.

## Documentation connexe

Dans notre base de connaissances de soutien :

* [ Configuration de paramètres DNS rapides sur les environnements d’évaluation et de production ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=fr)
* [ Configurez Fastly pour le forfait Starter sur le cloud ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html?lang=fr)
* [Blocs potentiels pour le lancement sur Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=fr)

Dans notre documentation destinée aux développeurs :

* [Aperçu rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=fr)
* [Go live checklist : configurations DNS pour Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=fr)
