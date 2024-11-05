---
title: Réduire les "oauth_tokens" expirés avant la mise à niveau 2.4.6
description: Cet article fournit une solution au problème où un grand nombre de "oauth_tokens" apparaissent dans la table "oauth_token", ce qui peut entraîner un long délai dans la mise à niveau vers la version 2.4.6. Il est recommandé de réduire la table `oauth_token` à l’aide de CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Réduire le `oauth_tokens` expiré avant la mise à niveau 2.4.6

Cet article fournit une solution au problème où un grand nombre de `oauth_tokens` apparaît dans votre table `oauth_token`, ce qui peut entraîner un long délai dans la mise à niveau vers la version 2.4.6. Il est recommandé de réduire la table `oauth_token` à l’aide de la tâche [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] pour supprimer les jetons expirés.

## Produits et versions concernés

* Adobe Commerce 2.4.0 - 2.4.6, toutes les méthodes de déploiement

## Problème

Si votre table `oauth_token` contient un grand nombre de `oauth_tokens`, cela peut entraîner un long délai dans la mise à niveau vers la version 2.4.6.

Le processus de mise à niveau comprend le chiffrement de ces jetons pour une couche de sécurité supplémentaire, et il n’a lieu que de 100 enregistrements à la fois. Cela peut prendre plusieurs heures s’il existe un grand nombre de jetons.

Réduire un grand nombre de `oauth_tokens` dans votre table `oauth_token` peut éviter un long délai dans la mise à niveau vers la version 2.4.6.

## Solution

Avant de commencer une mise à niveau, assurez-vous d’abord que la tâche [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] est en cours d’exécution. Elle réduit la taille de la table `oauth_token` en supprimant les jetons `oauth_tokens` expirés et doit déjà être activée par défaut.

Pour déclencher manuellement la tâche [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron], exécutez :
```bin/magento cron:run --group=default```

## Lecture connexe

* [Services > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) dans le guide de référence de configuration de Commerce
* [Guide d’authentification](https://developer.adobe.com/developer-console/docs/guides/authentication/) dans le guide Adobe Developer
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
