---
title: Réduire les "oauth_tokens" expirés avant la mise à niveau 2.4.6
description: Cet article fournit une solution au problème où un grand nombre de "oauth_tokens" apparaissent dans la table "oauth_token", ce qui peut entraîner un long délai dans la mise à niveau vers la version 2.4.6. Il est recommandé de réduire la table `oauth_token` à l’aide de CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Réduire les expirés `oauth_tokens` avant la mise à niveau 2.4.6

Cet article fournit une solution au problème où un grand nombre de `oauth_tokens` dans votre `oauth_token` , ce qui peut entraîner un long délai lors de la mise à niveau vers la version 2.4.6. Il est recommandé de réduire la variable `oauth_token` à l’aide du [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] pour supprimer les jetons expirés.

## Produits et versions concernés

* Adobe Commerce 2.4.0 - 2.4.6, toutes les méthodes de déploiement

## Problème

S’il existe un grand nombre de `oauth_tokens` dans votre `oauth_token` , ce qui peut entraîner un long délai dans la mise à niveau vers la version 2.4.6.

Le processus de mise à niveau comprend le chiffrement de ces jetons pour une couche de sécurité supplémentaire, et il n’a lieu que de 100 enregistrements à la fois. Cela peut prendre plusieurs heures s’il existe un grand nombre de jetons.

Réduire un grand nombre de `oauth_tokens` dans votre `oauth_token` peut éviter un long délai lors de la mise à niveau vers la version 2.4.6.

## Solution

Avant de commencer une mise à niveau, assurez-vous que la variable [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] est en cours d’exécution. Cela réduit la taille de la variable `oauth_token` en supprimant la table expirée `oauth_tokens` et doivent déjà être activés par défaut.

Pour déclencher manuellement l’événement [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] job, run :
```bin/magento cron:run --group=default```

## Lecture connexe

* [Services > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) dans le guide de référence de configuration de Commerce.
* [Guide d’authentification](https://developer.adobe.com/developer-console/docs/guides/authentication/) dans le guide Adobe Developer.
