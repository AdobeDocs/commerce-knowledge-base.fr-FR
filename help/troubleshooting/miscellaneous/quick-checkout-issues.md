---
title: Dépannage des problèmes de paiement rapide
description: Cet article explique les problèmes que vous pouvez rencontrer lors de l’utilisation de l’extension Achat rapide pour Adobe Commerce et fournit des solutions pour résoudre ces problèmes afin que vous puissiez utiliser l’extension.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Dépannage des problèmes de paiement rapide

Cet article explique les problèmes que vous pouvez rencontrer lors de l’utilisation de l’extension Achat rapide pour Adobe Commerce et fournit des solutions pour résoudre ces problèmes afin que vous puissiez utiliser l’extension.

## Produits et versions concernés

* La variable [Achat rapide](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) est compatible avec Magento Open Source et Adobe Commerce. Voir [Stratégie de cycle de vie](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) pour plus d’informations sur les versions prises en charge.

## Clés de compositeur incorrectes et stabilité minimale à `RC`

<u>Cause</u>:

Si le message d’erreur suivant s’affiche, vous pouvez disposer de clés de compositeur incorrectes :

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Solution</u>:

Vérifiez que vos clés de compositeur sont liées à la variable _ID de Magento_ utilisé lors de l’enregistrement du passage en caisse rapide.

Pour voir quelles clés de compositeur sont configurées :

1. Recherchez l’emplacement du `auth.json` fichier :

   ```bash
   composer config --global home
   ```

1. Afficher la variable `auth.json` fichier :

   ```bash
   cat /path/to/auth.json
   ```

1. Voir [les clés associées à votre ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Définissez la stabilité minimale sur `RC` dans le `composer.json` fichier .

   ```json
   "minimum-stability": "RC"
   ```

## Mémoire insuffisante pour PHP

<u>Cause</u>:

Si le message d’erreur suivant indique que vous n’avez pas assez de mémoire pour PHP :

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Solution</u>:

[Augmentation de la limite de mémoire](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) pour PHP sur votre environnement dans `php.ini`.

Vous pouvez également spécifier la limite de mémoire à l’aide de cette commande : `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Par exemple :

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Ajout de lignes d’adresse de rue avec une nouvelle adresse de livraison

Il existe un problème connu pour l’extension Achat rapide.

Lorsque vous [connexion avec un compte Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/), vous pouvez ajouter une nouvelle adresse de livraison avec une limite de 4 lignes par adresse de rue.

Si la nouvelle adresse de livraison contient plus de 4 lignes, elles ne seront pas stockées.

Adobe Commerce peut généralement être configuré pour prendre en charge jusqu’à 20 lignes d’adresses de rue.

## Comportement inattendu lorsque `Display Billing Address On` est défini sur `payment page`

Il existe un problème connu pour l’extension Achat rapide.

Si vous définissez la variable `Display Billing Address On` au paramètre `payment page` et [connexion avec un compte Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) lorsque vous cochez la variable `My billing and shipping address are the same` , le bouton radio s’affiche. `use existing card`. Comme l’adresse de facturation ne s’applique qu’aux nouvelles cartes de crédit, elle ne sera pas visible tant que l’utilisateur de la Bolt n’aura pas décidé d’ajouter une nouvelle option de carte de crédit.

Voir [Passage en caisse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) rubrique pour plus d’informations sur `Display Billing Address On` .
