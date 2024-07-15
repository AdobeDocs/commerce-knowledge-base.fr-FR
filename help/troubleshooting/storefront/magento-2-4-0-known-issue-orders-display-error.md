---
title: 'Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes'
description: "Cet article fournit une solution à un problème connu dans Adobe Commerce pour une erreur d’affichage des commandes. Lorsque les clients connectés examinent leurs commandes dans le menu **Mon compte** (**Mon compte &gt; Mes commandes**), la grille des commandes ne peut pas passer le nombre de commandes par page à 20 à partir de la page 2 lorsqu’il y a 11 commandes. En outre, s’il existe plus de commandes que de commandes configurées pour être affichées par page, lorsque vous accédez à la dernière page avec des commandes, la modification du nombre de commandes affichées par page génère le message d’erreur : *Vous n’avez passé aucune commande*. Ce problème sera résolu dans Adobe Commerce 2.4.1."
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes

Cet article fournit une solution à un problème connu dans Adobe Commerce pour une erreur d’affichage des commandes. Lorsque les clients connectés examinent leurs commandes dans le menu **Mon compte** (**Mon compte > Mes commandes**), la grille des commandes ne peut pas passer le nombre de commandes par page à 20 à partir de la page 2 lorsqu’il y a 11 commandes. En outre, s’il y a plus de commandes que de commandes configurées pour être affichées par page, lorsque vous accédez à la dernière page avec des commandes, la modification du nombre de commandes affichées par page génère le message d’erreur : *Vous n’avez pas passé de commandes*. Ce problème sera résolu dans Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables</u>

* Adobe Commerce 2.4.0 est installé.
* Créez au moins une catégorie et un produit simple.

<u>Étapes à reproduire</u>

1. Créez 11 commandes avec des produits.
1. Accédez à **Mon compte**.
1. Accédez à **Mes commandes**.
1. Cliquez sur la deuxième page pour afficher la 11e commande sur la grille des commandes.
1. Sélectionnez **Afficher = 20 par page** dans le menu déroulant.

<u>Résultat attendu</u>

Les 11 commandes s’affichent sur la première page, comme prévu.

<u>Résultat réel</u>

Le message d&#39;erreur *Vous n&#39;avez pas passé de commande* s&#39;affiche.

## Solution

La solution consiste à demander à l’acheteur de rouvrir la page **Mes commandes**, puis la liste des commandes s’affiche correctement. Le problème sera corrigé dans la prochaine version d’Adobe Commerce 2.4.1, qui sera publiée au quatrième trimestre 2020.

## Lectures connexes dans notre base de connaissances de support

* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
