---
title: 'ERREUR : échec du préchauffage sur Adobe Commerce sur l’infrastructure cloud'
description: 'Cet article fournit une solution pour le cas où le cache de page se réchauffe et échoue avec une erreur :'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
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
source-wordcount: '213'
ht-degree: 0%
---
# ERREUR : échec du préchauffage sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit une solution pour le cas où le cache de page se réchauffe et échoue avec une erreur :

*ERREUR : échec du préchauffage :`<website link>`*

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Échec de préchauffage du cache.

<u>Procédure à suivre </u> :

Démarrez les opérations de préchauffage du cache.

<u>Résultat attendu </u> :

Chargements de pages ou de sites entiers.

<u>Résultat réel</u> :

Le site n’est pas disponible ou le temps de réponse est trop long. *ERREUR : échec du préchauffage :`<website link>`*

## Cause

L’échauffement du cache ne fonctionne pas lorsque le contrôle d’accès HTTP est activé.

## Solution

Assurez-vous que le contrôle d’accès n’est pas activé : accédez à la branche/à l’environnement spécifique, cliquez sur l’icône **Paramètres**, puis vérifiez le paramètre **Contrôle d’accès HTTP** . Dans ce cas, le préchauffage du cache ne peut pas être effectué et le contrôle d’accès doit être désactivé.

## Lecture connexe

* [Guide de l’utilisateur d’Adobe Commerce > Cache pleine page](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) dans notre guide de l’utilisateur.
* [Préchauffage du cache et site indisponible sur Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) dans notre base de connaissances d’assistance.
