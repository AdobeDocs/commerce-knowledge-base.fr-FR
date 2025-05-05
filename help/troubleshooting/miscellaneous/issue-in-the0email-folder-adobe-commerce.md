---
title: Problème d’autorisation du dossier var/export Adobe Commerce sur le cloud
description: Cet article fournit une solution à un problème en raison duquel vous ne pouvez pas exporter les données de produit en raison d’un problème d’autorisation de fichier sur le serveur dans le dossier "var/export/email". Les symptômes incluent les exportations de produits et de catalogues non disponibles dans l’interface utilisateur, mais qui sont visibles lors de l’utilisation du SSH.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Problème d’autorisation du dossier var/export Adobe Commerce sur le cloud

Cet article fournit une solution à un problème en raison duquel vous ne pouvez pas exporter les données de produit en raison d’un problème d’autorisations de fichier sur le serveur dans le dossier `var/export/email`. Les symptômes incluent les exportations de produits et de catalogues non disponibles dans l’interface utilisateur, mais qui sont visibles lors de l’utilisation du SSH.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problème

Vous ne pouvez pas exporter de fichiers dans le dossier `var/export/email` ou `var/export/archive`.
Ce déploiement a échoué en raison des autorisations sur `var/export/email` ou `var/export/email/archive`, car ce dossier d’archive est créé sous courrier électronique et si je ne fais que l’exportation/le courrier électronique, il y a parfois toujours un problème) autre que l’ajout d’un élément pour tenir compte du sous-dossier `var/export/email/archive`.

<u>Étapes à reproduire</u> :

Dans l’administrateur, accédez à **Système** > *Transfert de données* > **Exporter**.
Sélectionnez les fichiers CSV à enregistrer dans le dossier `var/export/`.

<u>Résultat attendu</u> :

Les fichiers CSV sont visibles et peuvent être exportés.

<u>Résultat réel</u> :

Les fichiers CSV ne sont pas visibles. Un message de refus d’autorisation s’affiche également : *RecursiveDirectoryIterator::__build(/app/project id>/var/export/email) : échec de l’ouverture du répertoire : autorisation refusée*

Vous recevez le même message pour tous les types d’exportations : Advanced Prcing, Customer Finances, Customer Main File et Customer Addresses.

## Cause

Cela est dû à un dossier créé dans `/var` qui possède des autorisations imparfaites : `d-wxrwsr-T`. Le bit bascule T signifie que les utilisateurs peuvent uniquement supprimer les fichiers qu’ils détiennent, mais l’exécutable manquant signifie qu’ils ne peuvent pas créer de fichiers dans le répertoire .

Cela est souvent remarqué lorsque le système crée un dossier appelé `export`, contenant un dossier appelé `email`, contenant un dossier appelé `archive`.

Pour vérifier si le répertoire contient ces autorisations mal configurées, exécutez la commande suivante dans l’interface de ligne de commande/le terminal :

`ls -ld var/export/`

Si les autorisations sont mal configurées, la sortie sera :

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Solution

Pour résoudre ce problème, mettez à jour les autorisations des dossiers sur 777, puis tous les fichiers de manière récursive, en exécutant les commandes suivantes :

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Lecture connexe

* [Export](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/data-transfer/data-export) dans notre guide d’utilisation.
