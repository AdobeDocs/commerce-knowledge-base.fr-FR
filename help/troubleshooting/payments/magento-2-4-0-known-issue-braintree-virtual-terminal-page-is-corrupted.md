---
title: La page du terminal virtuel du Braintree Adobe Commerce 2.4.0 est corrompue
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.4.0, où la page Terminal virtuel du Braintree ne charge pas les éléments d’IU appropriés ou un message d’erreur approprié si Braintree n’est pas configuré.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# La page du terminal virtuel du Braintree Adobe Commerce 2.4.0 est corrompue

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.4.0, où la page Terminal virtuel du Braintree ne charge pas les éléments d’IU appropriés ou un message d’erreur approprié si Braintree n’est pas configuré.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

### Scénario 1 : le mode de paiement Braintree est configuré

<u>Étapes à reproduire :</u>

Dans Commerce Admin, accédez à **Sales** > **Braintree Virtual Terminal** . **&#x200B; **

<u>Résultat attendu :</u>

La page **Braintree Virtual Terminal** se charge avec l’interface utilisateur appropriée.

<u>Résultat réel :</u>

L’interface utilisateur de la page **Braintree Virtual Terminal** est endommagée.

### Scénario 2 : le mode de paiement du Braintree est configuré

<u>Étapes à reproduire :</u>

Dans Commerce Admin, accédez à **Sales** > **Braintree Virtual Terminal** . **&#x200B; **

<u>Résultat attendu :</u>

La page **Braintree Virtual Terminal** se charge avec l’interface utilisateur appropriée et un avertissement s’affiche pour vous informer que le Braintree n’est pas encore configuré.

<u>Résultat réel :</u>

L’interface utilisateur de la page **Braintree Virtual Terminal** est interrompue et aucun avertissement n’est affiché.

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
