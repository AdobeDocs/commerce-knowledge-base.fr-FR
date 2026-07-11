---
title: Les clients sont déconnectés ou perdent le contenu du panier sur le storefront Adobe Commerce
description: Cet article fournit une solution au problème de déconnexion ou de perte d’articles du panier sur le storefront, après avoir été redirigés vers la boutique Adobe Commerce à partir d’un paiement ou d’autres services tiers (cookie de session « se perd »).
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Les clients sont déconnectés ou perdent le contenu du panier sur le storefront Adobe Commerce

Cet article fournit une solution au problème de déconnexion ou de perte des articles du panier sur la vitrine, après leur redirection vers la boutique Adobe Commerce à partir du paiement ou d’autres services tiers (cookie de session « se perd »).

## Produits et versions concernés

* Adobe Commerce On-premise, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

<u>Procédure à suivre :</u>

1. Le client ajoute des produits au panier sur storefront et passe en caisse.
1. Le client est redirigé vers le site tiers pour le paiement/l’expédition ou d’autres informations/services.
1. Le client est redirigé vers le magasin .

<u>Résultat réel :</u>

Client redirigé vers le panier vide ou une page vierge.

<u>Résultat attendu : </u>

Le client est redirigé vers une page de paiement de succès (ou une autre page de succès), sans perdre les données et la progression du passage en caisse.

## Cause

L’attribut de cookie SameSite est défini sur *Lax* ou non spécifié (qui est traité comme défini sur *Lax* ). Avoir `SameSite` = *Lax* désactive le transfert d’un cookie vers des URL externes via des requêtes `POST`.

## Solution

Pour résoudre ce problème, contactez le fournisseur tiers et demandez à ses développeurs de mettre à jour leurs intégrations pour configurer les paramètres de cookie.

## Lecture connexe

[Mise à jour de Chrome SameSite](https://www.chromestatus.com/feature/5088147346030592)
