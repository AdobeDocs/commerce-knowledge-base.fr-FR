---
title: Les images mises en cache ne sont pas chargées après la mise à niveau de 2.2.X vers 2.3.X
description: Cet article fournit la solution au problème lié au fait que les images mises en cache ne s’affichent pas après la mise à niveau d’Adobe Commerce sur l’infrastructure cloud 2.2.X vers 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Les images mises en cache ne sont pas chargées après la mise à niveau de 2.2.X vers 2.3.X

Cet article fournit la solution au problème lié au fait que les images mises en cache ne s’affichent pas après la mise à niveau d’Adobe Commerce sur l’infrastructure cloud 2.2.X vers 2.3.X.

## Versions et éditions affectées :

* Adobe Commerce sur l’infrastructure cloud Formule Architecture 2.2.X, 2.3.X

## Problème

Une fois la mise à niveau d’Adobe Commerce de la version 2.2.X vers la version 2.3.X, les images de produit mises en cache ne sont pas disponibles et une page 404 s’affiche à la place.

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
   * Formule de démarrage : corrigez vous-même le fichier et repoussez les modifications.
   * Pro Plan :
   * Intégration : corrigez vous-même le fichier et effectuez les modifications.
   * Évaluation et production : corrigez le fichier vous-même, envoyez les modifications et créez un [ticket de support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour l’appliquer.

1. Activez l’optimisation d’image Fastly dans l’administrateur Commerce (la configuration Fastly doit être effectuée au préalable), comme décrit dans la section <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

Si la configuration est correcte, mais que vous rencontrez toujours le problème, continuez l’enquête ou contactez le [support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
