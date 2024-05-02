---
title: "Adobe Commerce 2.4.0 : erreur 404 - suppression des points de récompense lors du passage en caisse multi-livraison"
description: Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.0 pour une erreur de page web "*404 Not Found*" lors de la suppression de points de récompense sur une page de passage en caisse multi-expédition. Actuellement, sur la page de passage en caisse multi-expédition, lorsque vous tentez de supprimer les points de récompense utilisés pour payer une commande, une page "*404 Not Found*" s’affiche au lieu d’annuler des points de récompense réussis. Ce problème sera résolu dans avec une version de correctif Adobe Commerce 2.4.1.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 : erreur 404 lors de la suppression des points de récompense lors du passage en caisse multi-livraison

Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.0 pour une *404 Introuvable*&quot;erreur de page web lors de la suppression de points de récompense sur une page de passage en caisse multi-shipping. Actuellement, sur la page de paiement multi-expédition, lorsque vous tentez de supprimer les points de récompense utilisés pour payer une commande, un &quot;*404 Introuvable* &quot; s’affiche au lieu d’annuler des points de récompense. Ce problème sera résolu dans avec une version de correctif Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce 2.4.0 (toutes les méthodes de déploiement)

## Problème

<u>Étapes à reproduire</u>

1. Accédez au storefront et connectez-vous en tant que client.
1. Ajoutez au moins deux produits au **Panier**.
1. Ouvrez le **Panier**.
1. Cliquez sur le bouton **Afficher et modifier le panier** lien.
1. Cliquez sur le bouton **Extraction avec plusieurs adresses** lien.
1. Sélectionnez les adresses de livraison sur la page **Ship to Multiple Addresses** page.
1. Cliquez sur le bouton **Accéder aux informations d’expédition** bouton .
1. Sélectionnez la variable **Taux fixe - Mode de livraison fixe** pour chaque adresse.
1. Cliquez sur le bouton **Continuer vers les informations de facturation** bouton .
1. Vérifiez les **Utiliser vos points de récompense** de la **Informations de facturation** page.
1. Cliquez sur le bouton **Accédez à Réviser votre commande .** bouton .
1. Cliquez sur le bouton **Supprimer** lien de n’importe quelle adresse pour supprimer les points de récompense.

<u>Résultats attendus</u>

* La variable **Panier** s’affiche.
* Le &quot;*Vous avez supprimé les points de récompense de cet ordre.* &quot; doit apparaître.

<u>Résultat réel</u>

Un &quot;*404 Introuvable* &quot; s’affiche.

## Solution

La solution consiste à demander à l’acheteur de revenir au **Panier** et supprimez les points de récompense du **Panier** page web. Le problème devrait être corrigé dans le correctif Adobe Commerce version 2.4.1, qui doit être publié au 4e trimestre 2020.

## Lecture connexe

* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
