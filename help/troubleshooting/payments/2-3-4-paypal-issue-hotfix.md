---
title: 2.3.4 Correctif du problème PayPal
description: Cet article fournit un correctif pour les erreurs reçues lors du placement de commande lors de la sélection d’une région dans le paiement express PayPal. Le problème est dû aux modifications apportées à la version 2.3.4 d’Adobe Commerce et est lié à l’analyse des champs de l’adresse de paiement express de PayPal.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Correctif du problème PayPal

Cet article fournit un correctif pour les erreurs reçues lors du placement de commande lors de la sélection d’une région dans le paiement express PayPal. Le problème est dû aux modifications apportées à la version 2.3.4 d’Adobe Commerce et est lié à l’analyse des champs de l’adresse de paiement express de PayPal.

## Versions et produits concernés

* Adobe Commerce sur l’infrastructure cloud v2.3.4
* Adobe Commerce sur site v2.3.4

## Problème

Une erreur se produit lors de l’entrée dans le pays et la région lors du placement de la commande dans le paiement express PayPal. Le problème est reproductible pour tout pays où le champ de région dans la section de l’adresse est un champ de texte (par opposition à un menu déroulant).

<u>Étapes à reproduire</u> :

1. Activez le paiement express PayPal.
1. Ajoutez un produit au panier en tant qu’invité ou lorsque vous êtes connecté.
1. Allez à la caisse.
1. Sélectionnez votre adresse de livraison. Par exemple, *UK* . Saisissez ensuite une entrée dans le champ **Etat/Province**. Par exemple, *Nottinghamshire*.
1. Cliquez sur le bouton **Passer commande** pour passer commande. Vous obtenez une page de commande et un email de confirmation de commande.

<u>Résultat attendu :</u>

La commande est passée avec succès.

<u>Résultat réel :</u>

Lorsque vous cliquez sur le bouton de commande, une erreur s’affiche :

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Solution

Pour les commerçants sur site Adobe Commerce : appliquez le [correctif,](https://magento.com/tech-resources/download#download2353) disponible dans la section Téléchargements du portail [magento.com](https://magento.com) de mon compte.

Pour Adobe Commerce sur les marchands d’infrastructure cloud : Adobe a inclus le correctif dans les correctifs cloud pour Commerce v1.0.2. Reportez-vous aux [notes de mise à jour de Cloud Patches for Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) dans notre documentation destinée aux développeurs pour obtenir des instructions sur l’application du dernier package.

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Lecture connexe

* [Informations de mise à jour > Notes de mise à jour d’Adobe Commerce 2.3.4 > Appliquez le problème de paiement express PayPal avec le correctif régional pour Adobe Commerce 2.3.4 afin de résoudre un problème majeur de paiement express PayPal ](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) dans notre documentation destinée aux développeurs.
