---
title: Rediriger vers le formulaire de connexion de l’administrateur Commerce avec l’erreur "Votre compte est temporairement désactivé".
description: '"Cet article fournit les solutions possibles au problème de connexion de l’administrateur Commerce, où vous êtes redirigé vers le formulaire de connexion avec le message d’erreur suivant : *"Votre compte est temporairement désactivé"*. La solution suggérée est de vérifier et de corriger les paramètres de la base de données des utilisateurs administrateurs."'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Rediriger vers le formulaire de connexion de l’administrateur Commerce avec l’erreur &quot;Votre compte est temporairement désactivé&quot;.

Cet article fournit les solutions possibles au problème de connexion de l’administrateur Commerce, où vous êtes redirigé vers le formulaire de connexion avec le message d’erreur suivant : *&quot;Votre compte est temporairement désactivé&quot;*. La solution suggérée consiste à vérifier et à corriger les paramètres de la base de données des utilisateurs administrateurs.

## Éditions et versions affectées :

Toutes les versions et éditions Adobe Commerce

## Problème

<u>Étapes à reproduire</u> :

1. Accédez à la page d’administration de Commerce.
1. Saisissez vos informations d’identification, puis cliquez sur Se connecter.

<u>Résultat attendu</u> :

Vous êtes connecté à l’administrateur Commerce.

<u>Résultat réel</u> :

Vous êtes redirigé vers le formulaire de connexion, avec le message d’erreur suivant affiché : *&quot;Votre compte est temporairement désactivé. Réessayez ultérieurement&quot;*.

## Solution

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) ou accédez manuellement à la base de données à partir de la ligne de commande. Dans la table de base de données `admin_user`, pour votre enregistrement utilisateur administrateur, vérifiez si `is_active` est défini sur &quot;`1`&quot; et si `lock_expires` est `NULL`. Réinitialisez ces valeurs, le cas échéant.

## Lecture connexe dans notre base de connaissances de soutien

* [Redirigez-vous vers le formulaire de connexion sans erreur lorsque vous tentez de vous connecter à l’administrateur Commerce.](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
