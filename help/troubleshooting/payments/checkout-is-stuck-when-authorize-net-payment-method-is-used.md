---
title: Le passage en caisse est bloqué lorsque le mode de paiement Authorize.net est utilisé
description: Cet article fournit une explication et un correctif pour le problème d’Adobe Commerce 2.3.X où le passage en caisse est bloqué si Authorize.net est utilisé, avec le message d’erreur *'Cannot read property 'length' of null'* dans le journal de la console du navigateur.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Le passage en caisse est bloqué lorsque le mode de paiement Authorize.net est utilisé

Cet article fournit une explication et un correctif pour le problème d’Adobe Commerce 2.3.X où le passage en caisse est bloqué si Authorize.net est utilisé, avec le message d’erreur *&#39;Cannot read property &#39;length&#39; of null&#39;* dans le journal de la console du navigateur.

## Produits et versions concernés

* Adobe Commerce 2.3.X

>[!NOTE]
>
>L’intégration de paiement principale d’Adobe Commerce Authorize.Net est obsolète depuis la version 2.3.4 et a été complètement supprimée de la version 2.4.0. Utilisez plutôt une extension qui répond à vos besoins à partir de [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/).

## Problème

<u>Étapes à reproduire</u>

1. Configurez le Authorize.net mode de paiement dans l’administrateur Commerce.
1. Allez à la vitrine.
1. Ajoutez un produit au panier et passez à la caisse.
1. Choisissez Authorize.net comme mode de paiement.
1. Cliquez sur **Passer commande**.

<u>Résultat attendu</u>

L’iframe Authorize.net est chargé.

<u>Résultat réel</u>

Le compteur Ajax s’affiche et la page ne se charge jamais. L’erreur JS suivante s’affiche dans le journal de la console du navigateur : *’Uncaught TypeError: Cannot read property ’length’ of null at b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*)

## Cause

L’une des raisons les plus courantes de ce problème est que la clé du client public n’est pas spécifiée dans la configuration Authorize.Net de l’administrateur Commerce.

## Solution

Sous **Magasins** > **Paramètres** > **Configuration** > **Ventes** > **Méthodes de paiement**, dans la section **Authorize.net**, vérifiez si la valeur est spécifiée dans le champ **Clé client publique**. S’il est vide, saisissez la valeur de clé de votre compte marchand Authorize.Net.

Pour que les modifications soient appliquées, videz le cache en exécutant

```bash
bin/magento cache:clean
```
