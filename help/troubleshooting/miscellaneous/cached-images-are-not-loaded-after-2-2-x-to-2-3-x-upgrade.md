---
title: Les images mises en cache ne sont pas chargées après la mise à niveau 2.2.X vers 2.3.X
description: Cet article fournit la solution au problème d’affichage des images mises en cache après la mise à niveau d’Adobe Commerce sur les infrastructures cloud 2.2.X vers 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
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
source-wordcount: '287'
ht-degree: 0%
---
# Les images mises en cache ne sont pas chargées après la mise à niveau 2.2.X vers 2.3.X

Cet article fournit la solution au problème d’affichage des images mises en cache après la mise à niveau d’Adobe Commerce sur les infrastructures cloud 2.2.X vers 2.3.X.

## Versions et éditions concernées :

* Adobe Commerce sur les infrastructures cloud Pro plan architecture 2.2.X, 2.3.X

## Problème

Une fois Adobe Commerce mis à niveau de la version 2.2.X vers la version 2.3.X, les images du produit mises en cache ne sont pas disponibles et une page 404 s’affiche à la place.

Le problème est dû à une configuration Nginx incorrecte définie dans `.magento.app.yaml` : `index.php` (ou aucun) est utilisé pour l’emplacement `"/media"` au lieu de `passthru: /get.php`.

## Solution

1. Vérifiez votre fichier de configuration `.magento.app.yaml`, à l’emplacement `"/media"`. La configuration correcte ressemble à ce qui suit :

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Si `passthru` n’est pas défini sur `"/get.php"` et `expires` n’est pas défini, procédez comme suit.
1. Corrigez le fichier de configuration.
   * Plan de démarrage : corrigez le fichier vous-même et poussez les modifications.
   * Plan pro :
   * Intégration : corrigez le fichier vous-même et poussez les modifications.
   * Évaluation et production : corrigez vous-même le fichier, apportez les modifications et créez un [ticket d’assistance &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) pour l’appliquer.

1. Activez l’optimisation des images Fastly dans l’administration Commerce (Fastly doit être configuré au préalable), comme décrit dans la section <https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>.

Si la configuration est correcte, mais que vous rencontrez toujours le problème, poursuivez l’enquête ou contactez [l’assistance &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).
