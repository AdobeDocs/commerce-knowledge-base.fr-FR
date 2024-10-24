---
title: "Problème Adobe Commerce 2.4.0 : affichage des données de message brutes du storefront"
description: Cet article fournit une solution au problème lorsque tous les messages d’erreur sur le storefront s’affichent avec un signe "+" au lieu d’un espace. Cette solution permet de conserver la lisibilité des messages d’erreur.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Problème Adobe Commerce 2.4.0 : affichage des données de message brutes du storefront

Cet article fournit une solution au problème lorsque tous les messages d’erreur sur le storefront s’affichent avec un signe &quot;+&quot; au lieu d’un espace. Cette solution permet de conserver la lisibilité des messages d’erreur.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce sur site 2.4.0.

## Problème

<u>Étapes à reproduire :</u>

1. Accédez à la page **Créer un nouveau compte** sur le storefront.
1. Créez un compte à l’aide d’un email enregistré. Le message suivant s&#39;affiche :

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Cause

Le problème est dû à un problème PHP 7.4.2 lié aux cookies set\\read. Voir [BOGUE PHP \#79174 setcookie() encode l’espace comme \`+\`, mais $\_COOKIE ne les décode plus](https://bugs.php.net/bug.php?id=79174).

## Solution

Pour résoudre ce problème, utilisez une autre version de PHP 7.4.x. PHP 7.4.2 n’est pas pris en charge par Adobe Commerce 2.4.0.

## Lectures connexes dans notre base de connaissances de support :

* [Problème connu de Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
