---
title: Problèmes relatifs à la préparation des autorisations de fichier
description: "Cet article fournit un correctif pour les problèmes de vérification de l’état de préparation des autorisations de fichier. Les répertoires du système de fichiers Adobe Commerce doivent pouvoir être écrits par l’utilisateur du serveur web et le propriétaire du système de fichiers Adobe Commerce, le cas échéant. Une erreur similaire à celle-ci s’affiche dans l’assistant de configuration web si vos autorisations ne sont pas correctement définies :"
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Problèmes relatifs à la préparation des autorisations de fichier

Cet article fournit un correctif pour les problèmes de vérification de l’état de préparation des autorisations de fichier. Les répertoires du système de fichiers Adobe Commerce doivent pouvoir être écrits par l’utilisateur du serveur web et le propriétaire du système de fichiers Adobe Commerce, le cas échéant. Une erreur similaire à celle-ci s’affiche dans l’assistant de configuration web si vos autorisations ne sont pas correctement définies :

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

La manière dont vous résolvez le problème dépend de la configuration d’un utilisateur ou de deux utilisateurs :

* *Un utilisateur* signifie que vous vous connectez au serveur Adobe Commerce en tant qu’utilisateur qui exécute également le serveur web. Ce type de configuration est courant dans les environnements d’hébergement partagés.
* *Deux utilisateurs* signifie généralement que *cannot* connectez-vous en tant qu’utilisateur du serveur web ou basculez-vous vers . En règle générale, vous vous connectez en tant qu’utilisateur unique et exécutez le serveur web en tant qu’utilisateur différent. Cela est typique dans l’hébergement privé ou si vous disposez de votre propre serveur.

## Résolution d’un utilisateur

Si vous disposez d’un accès en ligne de commande, saisissez la commande suivante en supposant qu’Adobe Commerce soit installé dans `/var/www/html/magento2`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Si vous ne disposez pas d’un accès en ligne de commande, utilisez un client FTP ou une application de gestionnaire de fichiers fournie par votre fournisseur d’hébergement pour définir les autorisations.

## Résolution de deux utilisateurs

Si vous le souhaitez, saisissez toutes les commandes sur une seule ligne, en supposant qu’Adobe Commerce soit installé dans `/var/www/html/magento2` et le nom du groupe de serveurs web est `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Dans le système de fichiers d’événement, les autorisations sont définies de manière incorrecte et ne peuvent pas être modifiées par le propriétaire du système de fichiers Adobe Commerce. Vous pouvez saisir la commande en tant qu’utilisateur avec la variable `root` privilèges :

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
