---
title: Erreurs de déploiement pour lesquelles les correctifs sont introuvables
description: 'Cet article fournit une solution au problème d''erreur *Les correctifs suivants n''ont pas été trouvés : MDVA-XXXXX, ACSD-XXXXX. Vérifiez la disponibilité de la commande « status » de ces correctifs pour la version de Magento en cours*.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Erreurs de déploiement pour lesquelles les correctifs sont introuvables

Cet article fournit une solution au problème lors de la mise à niveau de votre instance. Le déploiement échoue et une erreur s’affiche dans les journaux de déploiement : *Les correctifs suivants n’ont pas été trouvés : MDVA-XXXXX, ACSD-XXXXX. Vérifiez la disponibilité de la commande « status » de ces correctifs pour la version Magento actuelle*.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problème

Une erreur se produit lors de la mise à niveau d’Adobe Commerce : *Les correctifs suivants sont introuvables*.

## Cause

Les correctifs précédemment appliqués pour vos anciennes versions ne sont pas applicables ou ne sont plus disponibles pour votre nouvelle version.

## Solution

1. Vérifiez votre fichier `.magento.env.yaml` sous la section QUALITY_PATCHES, par ex.,

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Recherchez les ID de correctif dans les [&#x200B; Notes de mise à jour des correctifs de qualité &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=fr) pour vérifier si chacun d’eux peut être appliqué à la nouvelle version d’Adobe Commerce vers laquelle vous effectuez la mise à niveau.
1. Si le correctif ne s’applique pas à la nouvelle version d’Adobe Commerce vers laquelle vous souhaitez effectuer la mise à niveau, supprimez l’ID de correctif du fichier `.magento.env.yaml`.
1. Une fois que vous avez révisé tous les identifiants de correctif indiqués par l’erreur, poussez les modifications et redéployez.

## Lecture connexe

* Guide [Application de correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr#apply-a-patch-in-a-local-environment) dans Commerce sur les infrastructures cloud.
