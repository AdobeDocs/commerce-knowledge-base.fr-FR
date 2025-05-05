---
title: '''Fastly Error : la version du module VCL est obsolète ! Veuillez recharger"'
description: Cet article fournit une solution pour lorsque le message "*Plugin VCL version est obsolète ! Transférez à nouveau.*" dans Configuration rapide, dans l’administrateur Commerce, en raison de l’absence de la dernière installation du module Fastly.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Erreur Fastly : la version du module externe VCL est obsolète ! Veuillez recharger

Cet article fournit une solution pour lorsque le message &quot;*La version du plug-in VCL est obsolète ! Transférez à nouveau.*&quot; dans Configuration rapide, dans l’administrateur Commerce, en raison de l’absence de la dernière installation du module Fastly.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.2.x., 2.3.x<br>
Fastly : cette erreur peut affecter toutes les versions du module Fastly, à l&#39;exception de la dernière. Pour plus d’informations sur la dernière version, voir [ Notes de mise à jour rapides ](https://github.com/fastly/fastly-magento2/releases) sur GitHub.

## Problème

1. Connectez-vous au panneau d’administration de Commerce.
1. Accédez à **Magasins** > **Configuration** > **Avancé** > **Système** > **Cache de page complète**   **Cache rapide.**
1. Dans la section **Chargement automatique et activation de service**, il y aura une &quot;*version du module externe VCL obsolète ! Transférez à nouveau.Notification &quot;0&rbrace;&quot;.*
1. Vous tentez de charger les fragments de code VCL en cliquant sur le bouton &quot;Télécharger VCL pour Fastly&quot;, mais vous voyez toujours l’avertissement &quot;*La version VCL du module externe est obsolète ! Veuillez recharger.*&quot;

## Cause

L’extension Fastly a été mise à jour (avec une configuration et des modèles VCL regroupés), mais la configuration VCL mise à jour n’a pas été téléchargée vers le service Fastly. Lorsque vous mettez à jour le module Adobe Commerce `Fastly_Cdn`, vous devez charger à nouveau une configuration VCL mise à jour vers Fastly.

## Solution

1. Vérifiez que vous avez installé les derniers outils de la CEE et dans la [version actuelle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html?lang=fr) de notre documentation destinée aux développeurs. Le module Outils/CEE a une version du module Fastly dans ses dépendances.

   Il ne s’agit peut-être pas de la dernière version du module externe Fastly, mais il est probable qu’il s’agisse d’une version ultérieure de celle que vous avez actuellement installée, et il est recommandé d’installer les derniers outils CEE-ONU.

1. Si vous n&#39;utilisez pas la version actuelle de CEE-Outils, suivez ces étapes pour [mettre à niveau](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=fr) dans notre documentation destinée aux développeurs.
1. Une fois que vous avez mis à niveau les outils ECID, vérifiez si vous disposez désormais d’une version actuelle du [module externe Fastly](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) installé.
1. Si le module externe Fastly n’est pas la version actuelle, procédez comme suit pour [mettre à niveau le module externe vers la version la plus récente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#upgrade-the-fastly-module) dans notre documentation destinée aux développeurs.

## Lecture connexe

* Pour plus d’informations sur la configuration et la configuration rapides, voir [Configuration des services rapides](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=fr) dans notre documentation destinée aux développeurs.
* Pour obtenir des informations générales sur Fastly, voir [fastly.com](https://www.fastly.com/).
