---
title: Rediriger vers le formulaire de connexion [!UICONTROL Commerce Admin] avec l’erreur « Votre compte est temporairement désactivé »
description: 'Cet article présente les solutions possibles au problème de connexion de l’administrateur Commerce. Le message d’erreur suivant s’affiche alors pour vous rediriger vers le formulaire de connexion : *« Votre compte est temporairement désactivé »*. La solution suggérée consiste à vérifier et à corriger les paramètres de la base de données des utilisateurs administrateurs.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
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
