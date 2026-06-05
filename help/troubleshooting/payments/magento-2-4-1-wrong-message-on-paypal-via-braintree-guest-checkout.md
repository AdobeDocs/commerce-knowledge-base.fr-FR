---
title: 'Adobe Commerce 2.4.1 : message incorrect lors du passage en caisse des invités PayPal-Braintree'
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1 où, si le passage en caisse des invités est désactivé, un client invité qui tente de passer une commande avec PayPal via Braintree reçoit un message d’erreur sans information.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 : message incorrect lors du passage en caisse des invités PayPal-Braintree

Cet article décrit un problème connu d’Adobe Commerce 2.4.1 où, si le passage en caisse des invités est désactivé, un client invité qui tente de passer une commande avec PayPal via Braintree reçoit un message d’erreur sans information.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0, 2.4.1
* Adobe Commerce sur les infrastructures cloud 2.4.0 et 2.4.1

## Problème

Une erreur non spécifique s’affiche lorsque la commande invité est désactivée à partir du serveur principal et que l’option de paiement PayPal via Braintree est sélectionnée dans le mini-panier ou le panier.

<u>Conditions préalables</u> :

1. Dans l’administration Commerce, sous **Magasins** > **Configuration** > **Ventes** > **Passage en caisse**, définissez **Autoriser le passage en caisse des invités** = *No*.
1. Activez PayPal via Braintree comme décrit dans la section [Braintree](https://experienceleague.adobe.com/fr/docs/commerce-admin/stores-sales/payments/braintree ?) de notre guide de l&#39;utilisateur.

<u>Procédure à suivre </u> :

1. Ajouter un produit au panier en tant qu’invité.
1. Sélectionnez **Mini-panier** et cliquez sur **Payer avec PayPal**.
1. Effectuez le passage en caisse de Paypal, puis vous arriverez sur la page d&#39;examen des commandes.
1. Sélectionnez **Mode d’expédition**.
1. Cliquez sur **Passer une commande**.

<u>Résultats attendus</u> :

Lorsqu&#39;un client clique sur le bouton PayPal de la page Mini-panier ou Panier, le message suivant doit s&#39;afficher :

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Si vous activez Direct Paypal sans utiliser Braintree, ce scénario se comporte différemment. Cela ne permet pas à l’utilisateur invité de poursuivre le processus de paiement. Le message suivant s&#39;affiche lorsque l&#39;utilisateur invité clique sur le bouton PayPal du mini-panier :

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Résultats réels</u> :

Le client est redirigé vers la page Panier et le message suivant s’affiche :

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Solution

La solution à ce problème est que le client peut se connecter à un magasin (les utilisateurs connectés n’utilisent pas le passage en caisse des invités). où le passage en caisse des invités est désactivé. Ce problème a été corrigé dans la version 2.4.2 d’Adobe Commerce.

## Lecture connexe

* [Bonne pratique pour le nombre de produits dans le panier dans Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) dans notre base de connaissances d’assistance.
* [Tutoriel sur le traitement des commandes : étape 1. Ajouter des articles au panier](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) dans notre documentation destinée aux développeurs
* Tutoriel de passage en caisse de [GraphQL : étape 1. Ajouter des produits au panier](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) dans notre documentation destinée aux développeurs
