---
title: 2.3.4 Correctif de problème PayPal
description: Cet article fournit un correctif pour les erreurs reçues lors du placement d'une commande lors de la sélection d'une région dans PayPal Express Checkout. Le problème est dû aux modifications apportées dans la version 2.3.4 d’Adobe Commerce et est lié à la manière dont les champs d’adresse de paiement PayPal Express sont analysés.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 2.3.4 Correctif de problème PayPal

Cet article fournit un correctif pour les erreurs reçues lors du placement d&#39;une commande lors de la sélection d&#39;une région dans PayPal Express Checkout. Le problème est dû aux modifications apportées dans la version 2.3.4 d’Adobe Commerce et est lié à la manière dont les champs d’adresse de paiement PayPal Express sont analysés.

## Versions et produits concernés

* Adobe Commerce sur les infrastructures cloud v2.3.4
* Adobe Commerce on-premise v2.3.4

## Problème

Une erreur se produit lors de l&#39;entrée du pays et de la région lors du placement de la commande dans PayPal Express Checkout. Le problème est reproductible pour tout pays où le champ Région de la section Adresse est un champ de texte (par opposition à un menu déroulant).

<u>Procédure à suivre </u> :

1. Activez PayPal Express Checkout.
1. Ajouter un produit au panier en tant qu’invité ou lorsque vous êtes connecté.
1. Accédez au passage en caisse.
1. Sélectionnez votre adresse de livraison. Par exemple, le *UK* . Saisissez ensuite une entrée dans le champ **État/Province**. Par exemple, *Nottinghamshire*.
1. Cliquez sur le bouton **Passer une commande** pour passer une commande. Vous obtenez une page de commande réussie et un e-mail de confirmation de commande.

<u>Résultat attendu : </u>

La commande a été passée.

<u>Résultat réel : </u>

Lorsque vous cliquez sur le bouton de commande, une erreur s’affiche :

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Solution

Pour les commerçants sur site Adobe Commerce : appliquez le correctif [hotfix](https://magento.com/tech-resources/download#download2353) disponible à partir de la section Téléchargements du portail [magento.com](https://magento.com) dans Mon compte.

Pour Adobe Commerce sur les commerçants d’infrastructure cloud : Adobe a inclus le correctif dans les correctifs cloud pour Commerce v1.0.2. Reportez-vous aux notes de mise à jour [Correctifs cloud pour Commerce](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&itm_medium=quick_search&itm_campaign=federated_search&itm_term=cloud%20patche) de notre documentation destinée aux développeurs pour obtenir des instructions sur l’application du dernier package.

## Application du correctif

Pour obtenir des instructions, consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) dans notre base de connaissances d’assistance.

## Lectures connexes

* [Informations sur la mise à jour > Notes de mise à jour d’Adobe Commerce 2.3.4 > Appliquer le problème de paiement PayPal Express avec le correctif de région pour Adobe Commerce 2.3.4 afin de résoudre un problème critique de paiement PayPal Express](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) dans notre documentation destinée aux développeurs.
