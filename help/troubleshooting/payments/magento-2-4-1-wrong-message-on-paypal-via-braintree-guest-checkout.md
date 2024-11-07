---
title: "Adobe Commerce 2.4.1 : message incorrect lors du passage en caisse des invités Braintree PayPal"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel si le passage en caisse des invités est désactivé, un client invité qui tente de passer une commande avec PayPal via Braintree reçoit un message d’erreur non informatif.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 : message incorrect lors du passage en caisse des invités Braintree PayPal

Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel si le passage en caisse des invités est désactivé, un client invité qui tente de passer une commande avec PayPal via Braintree reçoit un message d’erreur non informatif.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0, 2.4.1
* Adobe Commerce sur l’infrastructure cloud 2.4.0, 2.4.1

## Problème

Une erreur non spécifique s’affiche lorsque le passage en caisse des invités est désactivé depuis le serveur principal et que l’option de paiement par le Braintree PayPal est sélectionnée dans le mini-panier ou le panier.

<u>Conditions préalables</u> :

1. Dans l’administrateur Commerce, sous **Magasins** > **Configuration** > **Ventes** > **Passage en caisse**, définissez **Autoriser le passage en caisse des invités** = *Non*.
1. Activez PayPal via Braintree comme décrit dans le [Braintree](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?) de notre guide d’utilisation.

<u>Étapes à reproduire</u> :

1. Ajoutez un produit au panier en tant qu’invité.
1. Sélectionnez **Mini-cart** et cliquez sur **Payer avec PayPal**.
1. Effectuez le passage en caisse de Paypal, puis accédez à la page de vérification des commandes.
1. Sélectionnez **Méthode d’expédition**.
1. Cliquez sur **Passer commande**.

<u>Résultats attendus</u> :

Lorsqu’un client clique sur le bouton PayPal sur la page Mini-panier ou Panier, le message suivant doit s’afficher au client :

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Si vous activez la fonctionnalité Paypal direct sans utiliser Braintree, ce scénario se comporte différemment. Il ne permet pas à l’utilisateur invité de poursuivre le processus de paiement. Le message suivant s’affiche lorsque l’utilisateur invité clique sur le bouton PayPal dans le mini-panier :

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Résultats réels</u> :

Le client est redirigé vers la page Panier et le message suivant s’affiche :

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Solution

La solution à ce problème est que le client peut se connecter à un magasin (les utilisateurs connectés n’utilisent pas le paiement des invités) où le passage en caisse des invités est désactivé. Ce problème a été corrigé dans Adobe Commerce version 2.4.2.

## Lecture connexe

* [Bonne pratique pour le nombre de produits dans le panier dans Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) dans notre base de connaissances d’assistance.
* [Tutoriel sur le traitement des commandes : Étape 1. Ajoutez des éléments au panier ](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) dans notre documentation destinée aux développeurs.
* [Tutoriel de passage en caisse GraphQL : Étape 1. Ajout de produits au panier ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-add-product-to-cart.html) dans notre documentation destinée aux développeurs
