---
title: 'Erreur de déploiement : *erreur 7 lors du téléchargement... port 443 : connexion refusée*'
description: 'Cet article fournit une solution à l’erreur de déploiement : *« erreur 7 lors du téléchargement... port 443 : connexion refusée »*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: c005409900021a72d73c10a2df5f23be3f2bc2cf
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Erreur de déploiement : *erreur 7 lors du téléchargement... port 443 : connexion refusée*

Cet article fournit un correctif pour le problème lorsque le déploiement échoue avec le message d’erreur suivant :

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Versions affectées

Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problème

Le déploiement échoue avec un message d’erreur **curl error 7**.

<u>Procédure à suivre </u> :

Déclenchez un déploiement .

<u>Comportement attendu</u> :

Le déploiement a réussi.

<u>Comportement réel</u> :

Le déploiement échoue et l’erreur suivante : *curl error 7 while download ... port 443: Connection failed* s’affiche dans le journal de déploiement.

## Cause

Cela peut être dû à la perte de la connexion au cache pour le référentiel.

## Solution

Demandez à un super utilisateur du projet d’exécuter cette commande :

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Pour vérifier qui est un super utilisateur dans le projet, reportez-vous à la section [Afficher le rôle d’un utilisateur dans le projet](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) dans le guide Commerce sur les infrastructures cloud.

## Lecture recommandée

* [Résolution des problèmes de déploiement d’Adobe Commerce](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-29640).
* [Impossible d&#39;accéder au référentiel Adobe Commerce sur le cloud : erreur 403 Interdit ou 404 Introuvable lors du déploiement](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Échec du déploiement avec « Erreur lors de la création du projet : le hook de build a échoué avec le code d’état 1 »](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
