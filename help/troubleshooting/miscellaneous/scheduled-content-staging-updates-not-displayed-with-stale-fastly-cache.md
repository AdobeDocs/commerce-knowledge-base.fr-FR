---
title: Mises à jour de l’évaluation du contenu planifiées non affichées avec le cache fastidieux obsolète
description: Cet article fournit un correctif pour les cas où les magasins Adobe Commerce n’affichent pas les mises à jour planifiées lors de l’utilisation de Content Staging et Fastly. Le problème est dû à l’activation par défaut de la fonction Purge rapide des logiciels. Cette fonctionnalité réduit la charge des ressources de l’application et régénère uniquement un nouveau cache lors d’une seconde requête. Pour résoudre ce problème, vous pouvez activer la page Purge CMS via l’administrateur Commerce afin de toujours générer et diffuser du contenu neuf.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Mises à jour de l’évaluation du contenu planifiées non affichées avec le cache fastidieux obsolète

Cet article fournit un correctif pour les cas où les magasins Adobe Commerce n’affichent pas les mises à jour planifiées lors de l’utilisation de Content Staging et Fastly. Le problème est dû à l’activation par défaut de la fonction Purge rapide des logiciels. Cette fonctionnalité réduit la charge des ressources de l’application et régénère uniquement un nouveau cache lors d’une seconde requête. Pour résoudre ce problème, vous pouvez activer la page Purge CMS via l’administrateur Commerce afin de toujours générer et diffuser du contenu neuf.

## Problème

Mises à jour planifiées d’une ressource de contenu de magasin (page, produit, bloc, etc.) ne s’affichent pas sur storefront immédiatement après l’heure de début de la mise à jour. Cela se produit lorsque des mises à jour ont été planifiées à l’aide de la variable [Évaluation du contenu](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) .

## Cause

En raison de la fonctionnalité de purge douce de Fastly (activée par défaut), le storefront Adobe Commerce reçoit toujours l’ancien contenu (obsolète) mis en cache lors de l’envoi. **le premier** demande la ressource mise à jour à Fastly. Cela nécessite rapidement une seconde requête pour générer à nouveau les données du site.

Par conséquent, il se peut que la diffusion de contenu obsolète soit rapide jusqu’à la deuxième requête pour le contenu mis à jour.

**Mise en cache attendue :** Après avoir programmé une mise à jour d’une ressource de contenu à l’aide de l’évaluation de contenu, Adobe Commerce envoie une demande de mise à jour rapide du cache. Invalide rapidement le contenu mis en cache précédent (sans supprimer le contenu) et commence à diffuser le contenu mis à jour.

**Mise en cache réelle :** Si Fastly diffuse toujours le contenu obsolète lors de la réception **le premier** demande pour le contenu mis à jour, il n’enverra le contenu régénéré et correct qu’après réception de **la seconde** requête. Ce comportement a été mis en oeuvre pour réduire la charge du serveur en renouvelant le cache uniquement dans les zones à trafic avéré, sans régénérer le cache pour l’ensemble du site web. Mettez à jour le cache progressivement, en enregistrant les ressources de l’application.

## Solution

Si la diffusion de contenu obsolète même pour la première demande est inacceptable, vous pouvez désactiver la purge de l’effet élévateur et activer la page Purge CMS :

1. Connectez-vous à votre administrateur Commerce local en tant qu’administrateur.
1. Accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète**.
1. Développer **Configuration rapide**, puis développez **Avancé**.
1. Définir **Utilisation de la purge progressive** to *Non*.
1. Définir **Purge de la page CMS** to *Oui*.
1. Cliquez sur **Enregistrer la configuration** en haut de la page.


![purge_options.png](assets/purge_options.png)

## Documentation connexe

* [Configuration des options de purge](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans le guide Commerce on Cloud Infrastructure.
* [Évaluation du contenu](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) dans la documentation sur le contenu et la conception .
* [Diffusion de contenu obsolète](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) dans la documentation Fastly.
