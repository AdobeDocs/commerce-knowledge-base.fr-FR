---
title: Redirection de connexion lors de la tentative de connexion à l’administrateur Commerce
description: Cet article présente les solutions possibles au problème de connexion de l’administrateur Commerce, où vous êtes redirigé vers le formulaire de connexion lorsque vous tentez de vous connecter à l’administrateur et où aucun message d’erreur ne s’affiche. Il s’agit notamment de corriger les paramètres de fuseau horaire du serveur et d’effacer les paramètres des cookies dans Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Redirection de connexion lors de la tentative de connexion à l’administrateur Commerce

Cet article présente les solutions possibles au problème de connexion de l’administrateur Commerce, où vous êtes redirigé vers le formulaire de connexion lorsque vous tentez de vous connecter à l’administrateur et où aucun message d’erreur ne s’affiche. Il s’agit notamment de corriger les paramètres de fuseau horaire du serveur et d’effacer les paramètres des cookies dans Adobe Commerce.

## Éditions et versions affectées :

Toutes les versions et éditions Adobe Commerce.

## Problème

<u>Étapes à reproduire</u>:

1. Accédez à la page d’administration de Commerce.
1. Saisissez vos informations d’identification, puis cliquez sur Se connecter.

<u>Résultats attendus</u>:

Vous êtes connecté à l’administrateur Commerce.

<u>Résultats réels</u>:

Vous êtes redirigé vers le formulaire de connexion sans message d’erreur.

## Cause

Il existe plusieurs raisons à ce problème :

* Fuseau horaire incorrect défini au niveau du navigateur (ce qui entraîne la considéré comme ayant expiré la session d’administrateur même si sa durée de vie réelle n’a pas encore expiré).
* Paramètres des cookies incorrects, ce qui entraîne l’utilisation de la session établie par Adobe Commerce.

Consultez les paragraphes suivants pour chaque cas de solution.

## Solutions

### Problème de durée de vie de la session d’administrateur

Essayez d’utiliser un autre navigateur et augmentez la durée de vie de la session d’administration si elle est inférieure à une heure.

Pour augmenter la durée de vie de la session d’administration, procédez comme suit :

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)ou accéder manuellement à la base de données à partir de la ligne de commande pour exécuter la requête SQL suivante :

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Nettoyez le cache de configuration en exécutant la commande suivante :

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Paramètres des cookies incorrects

Pour vérifier les valeurs des paramètres des cookies et les effacer, procédez comme suit :

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)ou accéder manuellement à la base de données à partir de la ligne de commande pour exécuter la requête SQL suivante :

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

* [Rediriger vers le formulaire de connexion de l’administrateur avec l’erreur &quot;Votre compte est temporairement désactivé&quot;.](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) dans notre base de connaissances de soutien.
* [Rediriger vers le formulaire de connexion de l’administrateur avec l’erreur &quot;Votre session actuelle a expiré&quot;.](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) dans notre base de connaissances de soutien.
