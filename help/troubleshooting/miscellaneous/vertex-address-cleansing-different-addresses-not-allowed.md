---
title: 'Nettoyage des adresses de sommet : adresses différentes non autorisées'
description: 'Cet article présente la solution au problème suivant : lorsque l’utilisateur tente de saisir une adresse de facturation et d’expédition **différente** avec la validation d’adresse Vertex activée, le storefront ne le laisse pas saisir.'
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 7cf1167bce8cef51b206b6cc1d75214288f9cb1c
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Nettoyage des adresses de sommet : adresses différentes non autorisées

Cet article présente la solution au problème suivant : lorsque l’utilisateur tente de saisir une adresse de facturation et d’expédition **différente** avec la validation d’adresse Vertex activée, le storefront ne le laisse pas la saisir.

## Produits et versions concernés

* Adobe Commerce on-premise et Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

## Problème

<u>Procédure à suivre </u> :

1. Accédez à Admin > **Magasins** > **Configuration** > **Ventes** > **Nettoyage des adresses**.
1. Sélectionnez *Activé* dans la liste déroulante **Utiliser le nettoyage des adresses de sommet** et **Enregistrer la configuration**.
1. Accédez au serveur frontal en tant qu’invité et ajoutez un produit au panier.
1. Cliquez sur l’icône Panier et **Passer en caisse**.
1. Renseignez les champs d’adresse .
1. Sélectionnez le **Mode d&#39;expédition** souhaité, puis cliquez sur **Suivant**.
1. Cliquez de nouveau sur le bouton **Suivant**.
1. Décochez **Mon adresse de facturation et d’expédition** **sont identiques**, puis saisissez une nouvelle adresse de facturation (différente de l’adresse).
1. Cliquez sur le bouton **Mettre à jour**, puis sur **Mettre à jour l’adresse**.

<u>Résultats attendus</u> :

L’utilisateur voit différentes adresses de facturation et d’expédition.

<u>Résultats réels</u> :

Lorsque l’utilisateur clique sur mettre à jour, les adresses de facturation et d’expédition redeviennent identiques.

## Cause

Échec de la vérification de l&#39;adresse du sommet.

## Solution

Désactivez la vérification des adresses Vertex ou effectuez une mise à niveau vers la version 2.4.0.

## Lecture connexe

* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu dans Adobe Commerce 2.4.0 : les méthodes de paiement Braintree ne s’affichent pas lors du passage en caisse de plusieurs adresses](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 - Les taux de taxe à l’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : le bouton « Ajouter des sélections à mon panier » ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : libellé « Remboursement » manquant dans Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problème connu dans Adobe Commerce 2.4.0 : deux boutons manquants sur la page Créer une commande dans Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Problème connu d’Adobe Commerce 2.4.0 : lorsque Braintree est activé, problème de facture partielle Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problème connu dans Adobe Commerce 2.4.0 : message d’erreur lors de la sélection du mode de paiement local affiché pour certains pays lors du passage en caisse](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problème connu dans Adobe Commerce 2.4.0 : Amazon Pay activé, modes de paiement manquants lorsque le retour à la caisse standard est utilisé](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [problème connu d’Adobe Commerce 2.4.0 : l’installation de la version 2.4.0 échoue avec un cache de magasins obsolète](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
