---
title: Dépannage de l’installation des services de paiement
description: Cet article explique les erreurs que vous pouvez rencontrer lors de l’installation des services de paiement et fournit des solutions pour corriger ces erreurs afin que vous puissiez terminer l’installation.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Dépannage de l’installation des services de paiement

Cet article explique les erreurs que vous pouvez rencontrer lors de l’installation des services de paiement et fournit des solutions pour corriger ces erreurs afin que vous puissiez terminer l’installation.

## Produits et versions concernés

* [Les services de paiement](https://marketplace.magento.com/magento-payment-services.html) sont désormais compatibles avec les versions 2.4.0 à 2.4.4 d’Adobe Commerce.

## Problème : clés de compositeur incorrectes

Lors de l’installation de l’extension Pay Services, un message d’erreur peut s’afficher indiquant que vous avez utilisé des clés de compositeur incorrectes pendant l’installation.

<u>Étapes à reproduire</u> :

1. Tentez d’ [installer les services de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=fr).
1. Voir l’erreur suivante :

   *Impossible de trouver une version correspondante du package magento/payment-services. Vérifiez l&#39;orthographe du package, votre contrainte de version et que le package est disponible dans une stabilité correspondant à votre stabilité minimale (stable).*

<u>Résultat attendu</u> :

Vous pouvez suivre ces [instructions d’installation](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=fr) dans notre documentation destinée aux développeurs pour réussir l’installation des services de paiement.

<u>Résultat réel</u> :

Au cours de l’installation, un message d’erreur s’affiche indiquant que vous n’avez pas utilisé les clés de compositeur appropriées pendant l’installation.

### Cause

Vous avez utilisé des clés de compositeur incorrectes lors de l’installation.

### Solution

Vérifiez que [vos clés de compositeur sont liées à l’ID de Magento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=fr#incorrect-composer-keys) utilisé lors de l’enregistrement des services de paiement.

## Problème : utilisation du même espace de données sur plusieurs instances

Exécution d’une configuration multi-environnement avec des services de paiement sur chacun d’eux.

### Solution

La même clé API peut être utilisée sur plusieurs instances, mais chaque instance doit utiliser son propre espace de données SaaS.

Lorsque vous créez un projet SaaS, Commerce génère un ou plusieurs espaces de données SaaS en fonction de votre licence Commerce :

* Adobe Commerce : un espace de données de production ; deux espaces de données de test
* Magento Open Source : un espace de données de production ; aucun espace de données de test

Suivez les instructions de la section [Clé API Commerce et clé privée](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=fr#obtain-api-credentials) pour configurer correctement votre extension de services de paiement.

## Problème : mémoire insuffisante pour PHP

Lors de l’installation de l’extension Pay Services, un message d’erreur peut s’afficher indiquant que vous n’avez pas suffisamment de mémoire pour PHP.

<u>Étapes à reproduire</u> :

1. Tentez d’ [installer les services de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=fr).
1. Voir l’erreur suivante ou similaire :

   *Erreur fatale : taille de mémoire autorisée de 2146435072 octets épuisée (tentative d’allocation de 4 096 octets) dans phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php à la ligne 52*

<u>Résultat attendu</u> :

Vous pouvez suivre ces [instructions d’installation](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=fr) dans notre documentation destinée aux développeurs pour réussir l’installation des services de paiement.

<u>Résultat réel</u> :

Pendant l’installation, un message d’erreur s’affiche indiquant que vous n’avez pas assez de mémoire pour PHP.

### Cause

La limite pour PHP sur votre environnement n’est pas définie sur un seuil suffisamment élevé.

### Solution

[Augmentez la limite de mémoire pour PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=fr#not-enough-memory-for-php) sur votre environnement dans `php.ini`.
