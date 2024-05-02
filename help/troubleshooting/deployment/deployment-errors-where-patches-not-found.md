---
title: Erreurs de déploiement où des correctifs sont introuvables
description: '"Cet article fournit une solution au problème où une erreur s’affiche *Les correctifs suivants n’ont pas été trouvés : MDVA-XXXXX, ACSD-XXXXX. Veuillez vérifier avec la commande "status" la disponibilité de ces correctifs pour la version actuelle du Magento*."'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Erreurs de déploiement où des correctifs sont introuvables

Cet article fournit une solution au problème lors de la mise à niveau de votre instance. Le déploiement échoue et une erreur s’affiche dans les journaux de déploiement : *Les correctifs suivants sont introuvables : MDVA-XXXXX, ACSD-XXXXX. Vérifiez avec la commande &quot;status&quot; que ces correctifs sont disponibles pour la version actuelle du Magento.*.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problème

Vous rencontrez une erreur lors de la mise à niveau d’Adobe Commerce : *Les correctifs suivants sont introuvables*.

## Cause

Les correctifs précédemment appliqués pour vos anciennes versions ne sont pas applicables ou ne sont plus disponibles pour votre nouvelle version.

## Solution

1. Vérifiez vos `.magento.env.yaml` sous la section QUALITY_PATCH, par exemple,

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Recherchez les ID de correctif dans le [Notes de mise à jour sur les correctifs de qualité](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) pour vérifier si chacune d’elles peut être appliquée à la nouvelle version d’Adobe Commerce vers laquelle vous effectuez une mise à niveau.
1. Si le correctif ne s’applique pas à la nouvelle version d’Adobe Commerce vers laquelle vous souhaitez effectuer la mise à niveau, supprimez l’identifiant du correctif de la page `.magento.env.yaml` fichier .
1. Une fois que vous avez examiné tous les ID de correctif indiqués par l’erreur, redéployez les modifications et redéployez.

## Lecture connexe

* [Appliquer les correctifs](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) dans le guide d’infrastructure de Commerce on Cloud.
