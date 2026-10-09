---
title: 'Erreur de déploiement : *erreur 7 lors du téléchargement... port 443 : connexion refusée*'
description: 'Cet article fournit une solution à l’erreur de déploiement : *« erreur 7 lors du téléchargement... port 443 : connexion refusée »*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '286'
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

Pour vérifier qui est un super utilisateur dans le projet, reportez-vous à la section [Afficher le rôle d’un utilisateur dans le projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) dans le guide Commerce sur les infrastructures cloud.

## Lecture recommandée

* [Résolution des problèmes de déploiement d’](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-29640).
* [Impossible d&#39;accéder au référentiel Adobe Commerce sur le cloud : erreur 403 Interdit ou 404 Introuvable lors du déploiement](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Échec du déploiement avec « Erreur lors de la création du projet : le hook de build a échoué avec le code d’état 1 »](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
