---
title: "Problème Adobe Commerce 2.4.1 : impossible de modifier le compte Amazon dans Chrome"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel les clients se connectent aux comptes Amazon précédemment utilisés au lieu d’être invités à se connecter lors de l’utilisation de l’option Payer Amazon lors du passage en caisse.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Problème Adobe Commerce 2.4.1 : impossible de modifier le compte Amazon dans Chrome

Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel les clients se connectent aux comptes Amazon précédemment utilisés au lieu d’être invités à se connecter lors de l’utilisation de l’option Payer Amazon lors du passage en caisse.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.1
* Adobe Commerce sur l’infrastructure cloud 2.4.1

## Problème

Les clients sont connectés aux comptes Amazon précédemment utilisés au lieu d’être invités à se connecter lors de l’utilisation de l’option Payer Amazon lors de l’extraction.

<u>Étapes à reproduire :</u>

1. Sur le storefront, ajoutez tout article au panier et passez au passage en caisse des invités.
1. Cliquez sur le bouton **Amazon Pay** bouton . La fenêtre contextuelle de connexion Amazon.com s’affiche.
1. Connectez-vous au compte Amazon.
1. Sélectionnez une adresse et cliquez sur **Suivant**.
1. Sélectionnez le mode de paiement.
1. Cliquez sur **Passer commande**.
1. Revenez à la page d’accueil et connectez-vous au compte de magasin.
1. Ajoutez à nouveau n’importe quel article au panier et passez en caisse.
1. Cliquez sur le bouton **Amazon Pay** bouton .

<u>Résultat réel :</u>

Vous êtes de nouveau automatiquement connecté au compte Amazon précédemment utilisé (étape 3).

<u>Résultat attendu :</u>

La fenêtre contextuelle de connexion Amazon.com s’affiche et vous pouvez vous connecter ou créer un compte pour Amazon Pay.

## Cause

Le problème peut se produire dans l’une des situations suivantes :

* Lorsque la variable `SameSite` la valeur du cookie est `LAX`, le cookie ne sera pas envoyé dans le cadre d’appels tiers.
* La fonction de blocage de contenu Mozilla Firefox empêche des tiers de suivre les activités des utilisateurs du navigateur en bloquant l’utilisation des scripts et des mécanismes de stockage côté client. Firefox utilise un fournisseur externe, Disconnect.me pour fournir une liste des sites de suivi à bloquer. Amazon Pay utilise un iframe sur un site web tiers pour renvoyer un jeton d’accès après connexion et effectuer le rendu de l’adresse et du widget du portefeuille. Grâce à la fonction de blocage de contenu, les demandes de chargement d’iFrame payante d’Amazon sont considérées comme des demandes de suivi tierces et sont bloquées, ce qui empêche l’acheteur de procéder à l’extraction.
* Dans tous les cas où des cookies tiers ou JS sont explicitement bloqués par le navigateur.

## Solution

Assurez-vous que les demandes Amazon Pay Iframe ne sont pas bloquées par les navigateurs.
