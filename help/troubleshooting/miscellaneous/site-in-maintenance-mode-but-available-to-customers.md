---
title: Site en mode de maintenance mais disponible pour les clients
description: Cet article fournit un correctif pour le moment où le mode de maintenance est activé (problème d’infrastructure d’Adobe Commerce sur le cloud), mais le storefront est toujours disponible pour les clients.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '159'
ht-degree: 0%
---
# Site en mode de maintenance mais disponible pour les clients

Cet article fournit un correctif pour le moment où le mode de maintenance est activé (problème d’infrastructure d’Adobe Commerce sur le cloud), mais le storefront est toujours disponible pour les clients.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud (toutes versions)

## Problème

<u>Procédure à suivre :</u>

1. Activez le mode de maintenance pour le site.
1. Accédez au storefront.

<u>Résultat attendu : </u>

La page de maintenance s’affiche.

<u>Résultat réel :</u>

Les pages de la vitrine s’affichent comme d’habitude.

## Cause

Les pages étant toujours mises en cache, la page de maintenance ne s’affiche pas.

## Solution au site visible bien qu’en mode de maintenance

1. SSH vers votre environnement.
1. Exécutez la commande `php bin/magento cache:clean`.

## Lecture connexe

[Activez ou désactivez le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs.
