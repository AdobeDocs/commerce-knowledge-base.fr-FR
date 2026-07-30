---
title: Le paiement est bloqué lorsque le mode de paiement Authorize.net est utilisé
description: Cet article fournit une explication et un correctif pour le problème Adobe Commerce 2.3.X où le passage en caisse est bloqué si Authorize.net est utilisé, avec le message d’erreur *'Impossible de lire la propriété 'longueur' de null'* dans le journal de la console du navigateur.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Le paiement est bloqué lorsque le mode de paiement Authorize.net est utilisé

Cet article fournit une explication et un correctif pour le problème d’Adobe Commerce 2.3.X où le passage en caisse est bloqué si Authorize.net est utilisé, avec le message d’erreur *« Impossible de lire la propriété « longueur » de « null »* dans le journal de la console du navigateur.

## Produits et versions concernés

* Adobe Commerce 2.3.X

>[!NOTE]
>
>L’intégration de paiement principale Autoriser.Net d’Adobe Commerce est obsolète depuis la version 2.3.4 et a été complètement supprimée dans la version 2.4.0. Utilisez plutôt une extension d’Adobe Commerce [ [!DNL Marketplace]](https://commercemarketplace.adobe.com/) qui répond à vos besoins.

## Problème

<u>Procédure à suivre</u>

1. Configurez le mode de paiement Authorize.net dans l’administration Commerce.
1. Allez à la vitrine.
1. Ajoutez un produit au panier et passez en caisse.
1. Choisissez Authorize.net comme mode de paiement.
1. Cliquez sur **Passer une commande**.

<u>Résultat attendu</u>

L’iframe Authorize.net est chargé.

<u>Résultat réel</u>

La double flèche Ajax s’affiche et la page ne se charge jamais. L’erreur JS suivante s’affiche dans le journal de la console du navigateur : *&#39;Uncaught TypeError : Cannot read property &#39;length&#39; of null at b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Cause

L’une des raisons les plus courantes de ce problème est que la clé client publique n’est pas spécifiée dans la configuration Authorize.Net dans l’administrateur Commerce.

## Solution

Sous **Magasins** > **Paramètres** > **Configuration** > **Ventes** > **Modes de paiement**, dans la section **Autoriser.net**, vérifiez si la valeur est spécifiée dans le champ **Clé cliente publique**. S&#39;il est vide, saisissez la valeur de clé de votre compte marchand Authorize.Net.

Pour appliquer les modifications, nettoyez le cache en exécutant

```bash
bin/magento cache:clean
```
