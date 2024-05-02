---
title: 'Erreur de déploiement : *erreur 7 lors du téléchargement ... port 443 : connexion refusée*'
description: '''Cet article fournit une solution à l''erreur de déploiement : *"erreur 7 lors du téléchargement ... port 443 : connexion refusée"*.'''
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Erreur de déploiement : *erreur 7 lors du téléchargement ... port 443 : connexion refusée*

Cet article fournit un correctif pour le problème en cas d’échec du déploiement avec le message d’erreur suivant :

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Versions affectées

Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Échec du déploiement avec un **curl error 7** message.

<u>Étapes à reproduire</u>:

Déclenchez un déploiement.

<u>Comportement attendu</u>:

Le déploiement a réussi.

<u>Comportement réel</u>:

Le déploiement échoue et l’erreur suivante s’affiche : *erreur curl 7 lors du téléchargement ... port 443 : connexion refusée* apparaît dans le journal de déploiement.

## Cause

Cela peut être dû à la perte de la connexion au cache par le référentiel.

## Solution

Demandez à un super utilisateur du projet d’exécuter cette commande :

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Pour vérifier qui est un super utilisateur dans le projet, reportez-vous à la section [Affichage du rôle de projet d’un utilisateur](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) dans le guide Commerce on Cloud Infrastructure.

## Lecture recommandée

* [Dépannage du déploiement d’Adobe Commerce](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [Impossible d’accéder à Adobe Commerce sur le référentiel cloud : erreur 403 Forbidden ou 404 Not Found lors du déploiement](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Échec du déploiement avec &quot;Projet de création d’erreur : le crochet de génération a échoué avec le code d’état 1&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
