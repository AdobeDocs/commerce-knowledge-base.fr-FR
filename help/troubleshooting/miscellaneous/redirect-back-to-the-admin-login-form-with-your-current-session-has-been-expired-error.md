---
title: '''Rediriger vers le formulaire de connexion [!UICONTROL Commerce Admin] avec l’erreur "Votre session actuelle a expiré"'
description: '''Cet article fournit les solutions possibles au problème de connexion [!UICONTROL Commerce Admin], où vous êtes redirigé vers le formulaire de connexion avec le message d’erreur suivant : *"Votre session actuelle a expiré"*. Les solutions incluent la vérification des problèmes de définition de l’heure du serveur et la modification des paramètres de stockage de session."'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 3f205b1d755bda7056f47bf1e1d036feb47ebadd
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Rediriger vers le formulaire de connexion [!UICONTROL Commerce Admin] avec l’erreur &quot;Votre session actuelle a expiré&quot;.

Cet article fournit les solutions possibles au problème de connexion [!UICONTROL Commerce Admin], où vous êtes redirigé vers le formulaire de connexion avec le message d’erreur suivant : *&quot;Votre session actuelle a expiré&quot;*. Les solutions incluent la vérification des problèmes de définition de l’heure du serveur et la modification des paramètres de stockage de session.

## Éditions et versions affectées :

Toutes les versions et éditions Adobe Commerce

## Problème

<u>Étapes à reproduire</u> :

1. Accédez à la page **[!UICONTROL Commerce Admin]** .
1. Saisissez vos informations d’identification et cliquez sur **Se connecter**.

<u>Résultat attendu</u> :

Vous êtes connecté à [!UICONTROL Commerce Admin].

<u>Résultat réel</u> :

Vous êtes redirigé vers le formulaire de connexion, avec le message d’erreur suivant affiché : *&quot;Votre session actuelle a expiré&quot;*.

## Cause

Il peut y avoir deux raisons à ce problème :

* Correction d’un problème lié aux paramètres temporels du serveur
* un problème lié au stockage de session ;

Consultez la section suivante pour connaître les solutions.

## Solution

### Vérification des problèmes de paramètres de l’heure du serveur

Vérifiez l’enregistrement de session créé dans la table `admin_user_session`. Si les valeurs de `created_at` et/ou `updated_at` sont incorrectes, cela peut être dû au problème lié aux paramètres d’heure du serveur. Demandez à l’administrateur du système de serveur de vérifier cela. Notez que l’heure dans DB est définie sur UTC par défaut.

### Modification de l’enregistrement de session

Essayez de modifier le stockage de la session. Utilisez les informations de l’article [Comment localiser vos fichiers de session](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) dans notre documentation destinée aux développeurs pour savoir où est stockée votre session et modifiez-la en modifiant le fichier `app/etc/env.php`.

Par exemple, pour commencer à stocker une session dans le système de fichiers, modifiez la section `'session'` comme suit :

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Exécutez la commande `bin/magento app:config:import` pour importer des données de configuration.


## Lecture connexe

* [Importer des données à partir de fichiers de configuration](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) dans notre documentation destinée aux développeurs
* [Configurez [!DNL Redis]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) dans notre documentation destinée aux développeurs
* [Rediriger vers le formulaire de connexion [!UICONTROL Commerce Admin] avec l’erreur &quot;Votre compte est temporairement désactivé&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) dans notre base de connaissances de support
* [ Redirigez-vous vers le formulaire de connexion sans erreur, lorsque vous essayez de vous connecter à [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) dans notre base de connaissances de support.
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

