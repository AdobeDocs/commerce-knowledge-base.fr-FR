---
title: "Nettoyage des adresses de sommet : adresses différentes non autorisées"
description: Cet article traite de la solution au problème qui, lorsque l’utilisateur tente de saisir une adresse de facturation et d’expédition **différente**, avec la validation de l’adresse de sommet activée, le storefront ne permet pas à l’utilisateur de la saisir.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Nettoyage des adresses de sommet : adresses différentes non autorisées

Cet article traite de la solution au problème qui se produit lorsque l’utilisateur tente de saisir une **différent** l’adresse de facturation et d’expédition, avec la validation de l’adresse de sommet activée, le storefront ne permet pas à l’utilisateur de la saisir.

## Produits et versions concernés

* Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

## Problème

<u>Étapes à reproduire</u>:

1. Accédez à Admin > **Magasins** > **Configuration** > **Ventes** > **Nettoyage des adresses**.
1. Sélectionner *Activé* de la **Utiliser le nettoyage des adresses de sommet** et **Enregistrer la configuration**.
1. Positionnez-vous sur le front-end en tant qu&#39;invité et ajoutez un produit au panier.
1. Cliquez sur l’icône Panier et **Passez à l’extraction**.
1. Renseignez les champs de l&#39;adresse.
1. Sélectionnez le **Méthode d’expédition** et cliquez sur **Suivant**.
1. Cliquez sur le bouton **Suivant** à nouveau.
1. Décocher **Mon adresse de facturation et de livraison** **sont identiques**, puis saisissez une nouvelle adresse de facturation (différente de l’adresse).
1. Cliquez sur le bouton **Mettre à jour** , puis cliquez sur **Mettre à jour l&#39;adresse**.

<u>Résultats attendus</u>:

L’utilisateur voit différentes adresses de facturation et de livraison.

<u>Résultats réels</u>:

Lorsque l’utilisateur accède à la mise à jour, les adresses de facturation et de livraison redeviennent identiques.

## Cause

La vérification de l’adresse du sommet a échoué.

## Solution

Désactivez la vérification des adresses de sommet ou la mise à niveau vers la version 2.4.0.

## Lecture connexe

* [Problème connu d’Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur 404 lors de la suppression des points de récompense lors du passage en caisse multi-expédition](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les méthodes de paiement du Braintree ne s’affichent pas dans le passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu de création des libellés d’expédition dans Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton &quot;Ajouter des sélections à mon panier&quot; ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur le storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d&#39;Adobe Commerce 2.4.0 : absence de l&#39;étiquette &quot;Remboursement&quot; en larna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problème connu d’Adobe Commerce 2.4.0 : absence de deux boutons sur la page Créer une commande dans Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Problème connu d’Adobe Commerce 2.4.0 : lorsque Braintree est activé, problème de facture partielle de Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problème connu d’Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu d’Adobe Commerce 2.4.0 : paiement Amazon activé, méthodes de paiement manquantes lors du retour au paiement standard utilisé](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’installation 2.4.0 échoue avec le cache de magasins obsolète](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
