---
title: Mots de passe d’administrateur enregistrés en tant que texte brut dans le journal des actions
description: Cet article fournit un correctif pour lorsqu’un administrateur Commerce crée un utilisateur avec les privilèges d’administrateur et que le mot de passe est enregistré en texte brut dans la table de base de données "magento_logging_event_changes".
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Mots de passe d’administrateur enregistrés en tant que texte brut dans le journal des actions

Cet article fournit un correctif pour lorsqu’un administrateur Commerce crée un utilisateur avec les privilèges d’administrateur et que le mot de passe est enregistré en texte brut dans la table de base de données `magento_logging_event_changes`.

Pour résoudre ce problème de sécurité, installez la mise à jour de sécurité Adobe Commerce 2.0.16 et 2.1.9. Après avoir appliqué la mise à jour de sécurité, les mots de passe sont chiffrés et n’apparaissent pas en texte brut.

## Versions affectées {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce sur l’infrastructure cloud 2.X.X

## Problème {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Lorsqu’un administrateur Commerce existant crée un nouvel utilisateur avec les privilèges d’administrateur via **System** > **Permissions** > **All Users** > **Add new user**, le mot de passe (saisi en tant que confirmation) est enregistré en texte brut dans la table de base de données `magento_logging_event_changes`.

### Étapes à reproduire : {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Connectez-vous en tant qu’administrateur et créez un nouvel utilisateur en accédant à ce chemin d’accès : **Système** > Autorisations > **Tous les utilisateurs**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Cliquez ensuite sur la page **Ajouter un nouvel utilisateur** . Saisissez le mot de passe de l’administrateur actuel lorsque vous y êtes invité.
1. Accédez à la page **System** > **Action Log** > **Report** et recherchez la dernière entrée de journal.
1. Vous pouvez voir le mot de passe actuel, ni chiffré ni haché.

## Solution {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

L’installation de la [mise à jour de sécurité Adobe Commerce 2.0.16 et 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) corrige ce problème.

Après l&#39;installation de la mise à jour de sécurité, le mot de passe est chiffré et ne s&#39;affiche pas en texte brut dans la table `magento_logging_event_changes`.

## Plus d&#39;informations {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

* [Page de mise à jour de sécurité Adobe Commerce 2.0.16 et 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) dans notre centre de sécurité
* [Mettez à niveau l’application et les composants Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html?lang=fr) dans notre documentation destinée aux développeurs
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
