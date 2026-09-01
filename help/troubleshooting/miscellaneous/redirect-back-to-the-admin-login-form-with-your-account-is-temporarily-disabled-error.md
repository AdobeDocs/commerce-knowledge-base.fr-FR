---
title: Rediriger vers le formulaire de connexion [!UICONTROL Commerce Admin] avec l’erreur « Votre compte est temporairement désactivé »
description: 'Cet article présente les solutions possibles au problème de connexion de l’administrateur Commerce. Le message d’erreur suivant s’affiche alors pour vous rediriger vers le formulaire de connexion : *« Votre compte est temporairement désactivé »*. La solution suggérée consiste à vérifier et à corriger les paramètres de la base de données des utilisateurs administrateurs.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 9f4777deac8e9d367643158cf6947f4cb61e8fdd
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Rediriger vers le formulaire de connexion [!UICONTROL Commerce Admin] avec l’erreur « Votre compte est temporairement désactivé »

Cet article fournit les solutions possibles au problème de connexion [!UICONTROL Commerce Admin], où vous êtes redirigé(e) vers le formulaire de connexion avec le message d’erreur suivant : *« Votre compte est temporairement désactivé »*. La solution suggérée consiste à vérifier et à corriger les paramètres de la base de données des utilisateurs administrateurs.

## Éditions et versions concernées :

Toutes les versions et éditions d’Adobe Commerce

## Problème

<u>Procédure à suivre </u> :

1. Accédez à la page **[!UICONTROL Commerce Admin]** .
1. Saisissez vos informations d’identification et cliquez sur **Se connecter**.

<u>Résultat attendu </u> :

Vous êtes connecté à l’[!UICONTROL Commerce Admin] .

<u>Résultat réel</u> :

Vous êtes redirigé vers le formulaire de connexion, avec le message d’erreur suivant affiché : *Votre compte est temporairement désactivé. Réessayez plus tard »*.

## Solution

1. Créez une sauvegarde de base de données.
1. Utilisez un outil de base de données tel que [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou accédez manuellement à la base de données à partir de la ligne de commande. Dans le tableau de la base de données `admin_user`, pour l’enregistrement de votre utilisateur administrateur, vérifiez si `is_active` est défini sur « `1` » et `lock_expires` est `NULL`. Réinitialisez ces valeurs, si nécessaire.

## Lecture connexe

* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
