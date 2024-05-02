---
title: Les clients sont déconnectés ou le contenu du panier est perdu sur le storefront Adobe Commerce.
description: Cet article fournit une solution et une solution de contournement pour le problème, où les clients sont déconnectés ou perdent des articles du panier sur le storefront, après avoir été redirigés vers la boutique Adobe Commerce par paiement ou d’autres services tiers (le cookie de session "se perd").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Les clients sont déconnectés ou le contenu du panier est perdu sur le storefront Adobe Commerce.

Cet article fournit une solution au problème, où les clients sont déconnectés ou perdent des articles du panier sur le front de vente, après avoir été redirigés vers la boutique Adobe Commerce à partir de frais ou d’autres services tiers (le cookie de session &quot;se perd&quot;).

## Produits et versions concernés

* Adobe Commerce sur site, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

<u>Étapes à reproduire :</u>

1. Le client ajoute des produits au panier sur le storefront et procède au passage en caisse.
1. Le client est redirigé vers le site tiers pour le paiement/l’expédition ou d’autres informations/services.
1. Le client est redirigé vers le magasin.

<u>Résultat réel :</u>

Le client a été redirigé vers le panier vide ou une page vierge.

<u>Résultat attendu :</u>

Le client a été redirigé vers une page de paiement de succès (ou une autre page de succès), sans perdre les données de passage en caisse et la progression.

## Cause

L’attribut de cookie SameSite est défini sur *Lax* ou non spécifié (qui est traité comme défini sur *Lax* ). Après `SameSite` = *Lax* désactive le transfert d’un cookie vers des URL externes via `POST` requêtes.

## Solution

Pour résoudre ce problème, contactez le fournisseur de services tiers et demandez à ses développeurs de mettre à jour leurs intégrations afin de configurer les paramètres de cookie.

## Lecture connexe

[Mise à jour de Chrome SameSite](https://www.chromestatus.com/feature/5088147346030592)
