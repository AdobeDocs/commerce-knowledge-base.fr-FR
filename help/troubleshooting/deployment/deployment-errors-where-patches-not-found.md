---
title: Correctif introuvable erreurs lors du déploiement ou de l’application manuelle
description: 'Cet article fournit une solution au problème d''erreur *Les correctifs suivants n''ont pas été trouvés : MDVA-XXXXX, ACSD-XXXXX. Vérifiez la disponibilité de ces correctifs pour la version Magento actuelle à l’aide de la commande « status »*.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: be0c72a1759ba172666c7c9409c65a1a388e3f11
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Correctif introuvable erreurs lors du déploiement ou de l’application manuelle

Cet article fournit une solution au problème lors de la mise à niveau de votre instance. Le déploiement échoue et une erreur s’affiche dans les journaux de déploiement : *Les correctifs suivants n’ont pas été trouvés : MDVA-XXXXX, ACSD-XXXXX. Vérifiez la disponibilité de ces correctifs pour la version Magento actuelle à l’aide de la commande « status »*.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

Une erreur se produit lors de la mise à niveau d’Adobe Commerce : *Les correctifs suivants sont introuvables*.

## Cause

Les correctifs précédemment appliqués pour vos anciennes versions ne sont pas applicables ou ne sont plus disponibles pour votre nouvelle version.

Ce problème peut également se produire lorsque le package de l’outil de correctifs de qualité (`magento/quality-patches`) installé est obsolète.

Par exemple :

1er cas :
* Un correctif peut avoir été initialement disponible pour 2.4.7-p9 dans QPT 1.1.71
* Une version plus récente de QPT (par exemple, 1.1.72) peut ajouter ultérieurement la prise en charge de 2.4.7-p10
* Si le client ou la cliente met à niveau Commerce vers la version 2.4.7-p10, mais conserve une ancienne version de QPT installée, QPT peut ne pas reconnaître qu’une variante de correctif compatible existe pour la version 2.4.7-p10

2e cas :
* Un correctif peut avoir été ajouté dans QPT 1.1.72
* Si le client conserve une ancienne version de QPT installée, QPT ne reconnaîtra pas l’existence du correctif

Dans ce cas, l’application du correctif peut échouer avec un message tel que :

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

Cela se produit, car la version QPT installée ne peut pas mapper la version Commerce actuelle à une version applicable du correctif.

## Solution

Ce problème ne se limite pas aux déploiements qui appliquent des correctifs via `.magento.env.yaml`. Le même problème sous-jacent peut également se produire lors de l’application manuelle d’un correctif avec :

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

Par exemple :

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

Dans ce cas, le correctif n’est pas disponible pour la version d’Adobe Commerce installée dans l’environnement où la commande est exécutée.

1. Vérifiez votre fichier `.magento.env.yaml` sous la section QUALITY_PATCHES, par ex.,

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. Recherchez les ID de correctif dans les [&#x200B; Notes de mise à jour des correctifs de qualité &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=fr) pour vérifier si chacun d’eux peut être appliqué à la nouvelle version d’Adobe Commerce vers laquelle vous effectuez la mise à niveau.
1. Si le correctif ne s’applique pas à la nouvelle version d’Adobe Commerce vers laquelle vous souhaitez effectuer la mise à niveau, supprimez l’ID de correctif du fichier `.magento.env.yaml`.
1. Une fois que vous avez révisé tous les identifiants de correctif indiqués par l’erreur, poussez les modifications et redéployez.

## Lecture connexe

* Guide [Application de correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr#apply-a-patch-in-a-local-environment) dans Commerce sur les infrastructures cloud.

