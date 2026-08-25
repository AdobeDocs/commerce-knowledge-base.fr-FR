---
title: Redirection de connexion lors de la tentative de connexion à Commerce Admin
description: Cet article présente les solutions possibles au problème de connexion d’administrateur Commerce. Lorsque vous tentez de vous connecter à l’administrateur, vous êtes redirigé vers le formulaire de connexion et aucun message d’erreur ne s’affiche. Il s’agit notamment de corriger les paramètres de fuseau horaire du serveur et d’effacer les paramètres des cookies dans Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: ec2111316458420c51a6b6f3b3881bd3f9d10c06
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Redirection de connexion lors de la tentative de connexion à Commerce Admin

Cet article présente les solutions possibles au problème de connexion d’administrateur Commerce. Lorsque vous tentez de vous connecter à l’administrateur, vous êtes redirigé vers le formulaire de connexion et aucun message d’erreur ne s’affiche. Il s’agit notamment de corriger les paramètres de fuseau horaire du serveur et d’effacer les paramètres des cookies dans Adobe Commerce.

## Éditions et versions concernées :

Toutes les versions et éditions d’Adobe Commerce.

## Problème

<u>Procédure à suivre </u> :

1. Accédez à la page d’administration Commerce.
1. Saisissez vos informations d’identification et cliquez sur Connexion.

<u>Résultats attendus</u> :

Vous êtes connecté à l’administrateur Commerce.

<u>Résultats réels</u> :

Vous êtes redirigé vers le formulaire de connexion sans message d’erreur.

## Cause

Il existe plusieurs raisons possibles à ce problème :

* Fuseau horaire incorrect défini au niveau du navigateur (ce qui fait que la session d’administration est considérée comme expirée même si sa durée de vie réelle n’a pas encore expiré).
* Paramètres des cookies incorrects, ce qui fait que la session établie n’est pas utilisée par Adobe Commerce.

Voir les paragraphes suivants pour obtenir des solutions dans chaque cas.

## Solutions

### Problème de durée de vie d’une session d’administrateur

Essayez d’utiliser un autre navigateur et augmentez la durée de vie de la session d’administration si elle est inférieure à une heure.

Pour augmenter la durée de vie de la session d’administration, procédez comme suit :

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou accédez manuellement à la base de données à partir de la ligne de commande pour exécuter la requête SQL suivante :

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Nettoyez le cache de configuration en exécutant la commande suivante :

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Paramètres de cookies incorrects

Pour vérifier les valeurs des paramètres des cookies et les effacer, procédez comme suit :

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou accédez manuellement à la base de données à partir de la ligne de commande pour exécuter la requête SQL suivante :

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Si les réponses des valeurs ne sont pas vides, définissez-les sur NULL en exécutant :

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Nettoyez le cache de configuration en exécutant la commande suivante :

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Articles connexes

* [Redirigez-vous vers le formulaire de connexion d’administrateur avec l’erreur « Votre compte est temporairement désactivé »](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) dans notre base de connaissances de l’assistance.
* [Redirigez-vous vers le formulaire de connexion d’administrateur avec l’erreur « Votre session en cours a expiré »](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-41686) dans notre base de connaissances d’assistance.
