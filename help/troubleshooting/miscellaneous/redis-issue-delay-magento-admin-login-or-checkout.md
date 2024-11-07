---
title: Redis le délai de connexion ou d’extraction de Commerce Admin
description: Cet article fournit un correctif pour le problème lors de la connexion à l’administrateur Commerce ou de l’ouverture de la page de passage en caisse qui entraîne un délai ou un délai d’expiration (plus de 30 secondes). Le problème se produit lorsque Redis est utilisé pour le stockage de session.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Redis le délai de connexion ou d’extraction de Commerce Admin

Cet article fournit un correctif pour le problème lors de la connexion à l’administrateur Commerce ou de l’ouverture de la page de passage en caisse qui entraîne un délai ou un délai d’expiration (plus de 30 secondes). Le problème se produit lorsque Redis est utilisé pour le stockage de session.

**Cause :**   [Problème Github \#12385](https://github.com/magento/magento2/issues/12385).

**Solution :** mise à jour vers le dernier correctif Adobe Commerce pour corriger ces problèmes pour toutes les versions de Redis et versions spécifiques d’Adobe Commerce.

## Versions et technologies affectées

* Adobe Commerce sur les versions d’infrastructure cloud 2.1.11 - 2.1.13 et 2.2.1
* Adobe Commerce sur site versions 2.1.11 - 2.1.13 et 2.2.1
* Redis, toutes versions

Si vous utilisez Adobe Commerce sur la version [2.2.0](#h_64593789291526919876198) de l&#39;infrastructure cloud, une solution de contournement est disponible.

## Problème

La connexion à l’administrateur Commerce ou le passage à la page de passage en caisse dure plus de 30 secondes.

Cela ne se produit que lorsque les sessions utilisateur sont stockées dans Redis.

## Cause

Adobe Commerce a rencontré un problème avec le mécanisme de verrouillage de session qui a ajouté un délai d’expiration de 30 secondes à certaines opérations lorsque Redis était utilisé pour le stockage de session. Pour plus d’informations, voir le [problème Github \#12385](https://github.com/magento/magento2/issues/12385).

Ce problème a été corrigé dans Adobe Commerce 2.1.14 et 2.2.2.

## Solutions : correctif ou mise à niveau

### Solution 1 : appliquez le correctif avec un correctif

Pour recevoir un correctif, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant le correctif. Dans votre ticket, indiquez votre version Adobe Commerce et le numéro de référence correspondant au correctif :

* **2.1.11 et versions ultérieures :** MDVA-7835
* **2.2.1 :** MDVA-8128

Le numéro de référence général (indépendant de la version) est MAGETTwo-84289.

### Solution 2 : effectuez une mise à niveau vers 2.1.14/2.2.2 ou une version ultérieure

Si vous avez envisagé d’effectuer une mise à niveau vers Adobe Commerce 2.2.2 ou une version ultérieure, vous pouvez saisir cette opportunité de mise à jour pour résoudre le problème.

## Solution : désactiver le verrouillage de session

Pour désactiver le verrouillage de session, définissez `disable_locking` sur `1` dans la section de configuration Redis du fichier `env.php` :

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Cette solution n’affecte aucune autre fonctionnalité d’Adobe Commerce.

### Rétablir la solution après l’application du correctif

Après avoir appliqué le correctif avec le correctif, la solution n’est plus nécessaire. Vous pouvez donc l’annuler (définissez `disable_locking` sur `0`).

## Adobe Commerce sur l’infrastructure cloud 2.2.0 : utilisez les outils CEE v2002.0.8 ou version ultérieure {#h_64593789291526919876198}

Le package de script de déploiement [CEE-Outils](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) avec les versions 2002.0.3 à 2002.0.7 [ applique automatiquement la solution de contournement, en définissant `disable_locking` sur `1`. ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) Cela désactive le mécanisme de verrouillage de session pour Adobe Commerce 2.2.0, sur lequel le problème d’origine ne se produit pas.

Si vous exécutez Adobe Commerce sur l’infrastructure de cloud 2.2.0, mettez à niveau les outils de CEE vers la version 2002.0.8 de la version ultérieure. Vous pouvez également envisager de mettre à niveau votre Adobe Commerce sur l’infrastructure cloud vers la version 2.2.2 ou ultérieure.
