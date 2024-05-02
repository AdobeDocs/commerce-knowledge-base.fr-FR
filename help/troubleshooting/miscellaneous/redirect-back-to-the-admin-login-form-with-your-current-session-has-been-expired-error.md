---
title: Rediriger vers le formulaire de connexion de l’administrateur Commerce avec l’erreur "Votre session actuelle a expiré".
description: '"Cet article présente les solutions possibles au problème de connexion de l’administrateur Commerce, où vous êtes redirigé vers le formulaire de connexion avec le message d’erreur suivant : *"Votre session actuelle a expiré"*. Les solutions incluent la vérification des problèmes de définition de l’heure du serveur et la modification des paramètres de stockage de session."'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Rediriger vers le formulaire de connexion de l’administrateur Commerce avec l’erreur &quot;Votre session actuelle a expiré&quot;.

Cet article présente les solutions possibles au problème de connexion de l’administrateur Commerce, où vous êtes redirigé vers le formulaire de connexion avec le message d’erreur suivant : *&quot;Votre session actuelle a expiré&quot;*. Les solutions incluent la vérification des problèmes de définition de l’heure du serveur et la modification des paramètres de stockage de session.

## Éditions et versions affectées :

Toutes les versions et éditions Adobe Commerce

## Problème

<u>Étapes à reproduire</u>:

1. Accédez à la page d’administration de Commerce.
1. Saisissez vos informations d’identification, puis cliquez sur Se connecter.

<u>Résultat attendu</u>:

Vous êtes connecté à l’administrateur Commerce.

<u>Résultat réel</u>:

Vous êtes redirigé vers le formulaire de connexion, avec le message d&#39;erreur suivant affiché : *&quot;Votre session actuelle a expiré&quot;*.

## Cause

Il peut y avoir deux raisons à ce problème :

* Correction d’un problème lié aux paramètres temporels du serveur
* un problème lié au stockage de session ;

Consultez la section suivante pour connaître les solutions.

## Solution

### Vérification des problèmes de paramètres de l’heure du serveur

Vérifiez l’enregistrement de session créé dans le `admin_user_session` table. Si les valeurs de `created_at` et/ou `updated_at` sont incorrectes, cela peut être dû au problème lié aux paramètres de l’heure du serveur. Demandez à l’administrateur du système de serveur de vérifier cela. Notez que l’heure dans DB est définie sur UTC par défaut.

### Modification de l’enregistrement de session

Essayez de modifier le stockage de la session. Utilisez les informations de la [Comment localiser vos fichiers de session](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) article dans notre documentation destinée aux développeurs pour savoir où est stockée votre session, puis modifiez-la en modifiant le `app/etc/env.php` fichier .

Par exemple, pour commencer à stocker une session dans le système de fichiers, modifiez la variable `'session'` comme suit :

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Exécutez la variable `bin/magento app:config:import` pour importer des données de configuration.


## Lecture connexe

* [Importation de données à partir de fichiers de configuration](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) dans notre documentation destinée aux développeurs
* [Configuration de Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) dans notre documentation destinée aux développeurs
* [Rediriger vers le formulaire de connexion de l’administrateur Commerce avec l’erreur &quot;Votre compte est temporairement désactivé&quot;.](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) dans notre base de connaissances de soutien
* [Redirigez-vous vers le formulaire de connexion sans erreur lorsque vous tentez de vous connecter à l’administrateur Commerce.](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) dans notre base de connaissances de soutien
