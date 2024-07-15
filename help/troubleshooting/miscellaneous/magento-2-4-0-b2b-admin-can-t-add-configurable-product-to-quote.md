---
title: L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis
description: Cet article traite d’un problème connu dans l’administrateur Commerce lors de la gestion d’une citation B2B. Il n’est pas possible d’ajouter un produit configurable par **SKU** au guillemet. Lorsque vous cliquez sur le bouton **Ajouter à la citation**, la page d’édition **Citation** est bloquée et vous ne pouvez pas configurer le produit ni enregistrer les modifications. Ce problème se produit également dans l’administration lors de l’ajout d’un produit par **SKU** à une commande ou de l’ajout d’un produit par **SKU** dans **Advanced Checkout** (**Admin** &gt; **Customers** &gt; **Tous les clients**> **Customer Edit &gt; (). Ce problème sera résolu dans un correctif pour Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# L’administrateur d’Adobe Commerce 2.4.0 B2B ne peut pas ajouter de produit configurable pour le devis

Cet article traite d’un problème connu dans l’administrateur Commerce lors de la gestion d’un devis B2B. Il n’est pas possible d’ajouter un produit configurable par **SKU** au guillemet. Lorsque vous cliquez sur le bouton **Ajouter à la citation** , la page d’édition **Citation** est bloquée et vous ne pouvez pas configurer le produit et enregistrer les modifications. Ce problème se produit également dans l’administration lors de l’ajout d’un produit par **SKU** à une commande ou de l’ajout d’un produit par **SKU** dans **Advanced Checkout** (**Admin** > **Customers** > **All Customers** > **Customer Edit** > Manage **Panier**). Ce problème sera résolu dans un correctif pour Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables</u>

* Adobe Commerce 2.4.0 est installé.
* B2B est installé.
* Définissez les fonctionnalités B2B sur **Activer la société =** *Oui* , **Activer le catalogue partagé =** *Non* et **Activer le devis B2B =** *Oui*.
* Créez un compte client.
* Créez un compte de société avec le client créé précédemment en tant qu’administrateur de société.
* Créez un produit simple (par exemple : name &amp; **SKU** = TEST SIMPLE 1) qui n’est pas affecté à **Default (General)**.
* Demandez à l’administrateur de l’entreprise de demander un devis à l’aide du produit simple créé ci-dessus (exemple : TEST SIMPLE 1).

<u>Étapes à reproduire</u>

1. Accédez au panneau d’administration de Commerce.
1. Accédez à **Ventes > Guillemets**.
1. Ouvrez la **citation**.
1. Cliquez sur le bouton **Ajouter un produit par SKU** .
1. Saisissez le **SKU** d’un autre produit (par exemple : TEST SIMPLE 2) dans le champ de saisie **Saisir le SKU**.
1. Entrez une quantité valide dans le champ d’entrée **Qté**.
1. Cliquez sur le bouton **Ajouter à la citation** .

<u>Résultats attendus</u>

* La grille **Produits non ajoutés à la citation**, contenant le nom et la **SKU** du produit créé, s’affiche comme prévu.
* Une fois le produit configuré, l’administrateur peut l’ajouter à la **citation** en cliquant sur le bouton **Ajouter des produits à la citation** , comme prévu.

<u>Résultats réels</u>

* La grille **Produits non ajoutés à la citation**, contenant le nom et la **SKU** du produit créé, n’apparaît pas.
* La page **Citation** est bloquée lors du chargement.

## Recommandation

Actuellement, il n’existe aucune solution pour ce problème avec l’édition de citations B2B, mais pour la gestion des commandes et des paniers, il est possible de sélectionner des produits dans la **liste de produits** au lieu de les ajouter par **SKU**. Un correctif pour résoudre le problème sera disponible pour Adobe Commerce 2.4.1, qui doit être publié au quatrième trimestre 2020.

## Lecture connexe

* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : affichage des données de message brutes sur Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe d’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : erreur d’affichage des commandes](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
