---
title: Les clients sont déconnectés ou perdent le contenu du panier sur le storefront Adobe Commerce
description: Cet article fournit une solution au problème de déconnexion ou de perte d’articles du panier sur le storefront, après avoir été redirigés vers la boutique Adobe Commerce à partir d’un paiement ou d’autres services tiers (cookie de session « se perd »).
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
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
