---
title: L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis
description: Cet article aborde un problème connu dans Commerce Admin lors de la gestion d’un devis B2B. Il n’est pas possible d’ajouter un produit configurable par **SKU** au devis. Lorsque vous cliquez sur le bouton **Ajouter au devis**, la page de modification du **Devis** est bloquée et vous ne pouvez pas configurer le produit ni enregistrer les modifications. Ce problème se produit également dans Admin lors de l’ajout d’un produit par **SKU** à une commande ou de l’ajout d’un produit par **SKU** dans **Passage en caisse avancé** (**Admin** &gt; **Clients** &gt; **Tous les clients** &gt; **Modification du client** &gt; **Gérer le panier**). Ce problème sera résolu dans un correctif pour Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# L’administrateur B2B d’Adobe Commerce 2.4.0 ne peut pas ajouter de produit configurable au devis

Cet article aborde un problème connu dans Commerce Admin lors de la gestion d’un devis B2B. Il n’est pas possible d’ajouter un produit configurable par **SKU** au devis. Lorsque vous cliquez sur le bouton **Ajouter au devis**, la page de modification du **Devis** est bloquée et vous ne pouvez pas configurer le produit ni enregistrer les modifications. Ce problème se produit également dans Admin lors de l’ajout d’un produit par **SKU** à une commande ou de l’ajout d’un produit par **SKU** dans **Passage en caisse avancé** (**Admin** > **Customers** > **All Customers** > **Customer Edit** > **Gérer le panier**). Ce problème sera résolu dans un correctif pour Adobe Commerce 2.4.1.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

<u>Conditions préalables </u>

* Adobe Commerce 2.4.0 est installé.
* B2B est installé.
* Définissez les fonctionnalités B2B sur **Activer la société =** *Oui* , **Activer le catalogue partagé =** *Non* et **Activer le devis B2B =** *Oui*.
* Créez un compte client.
* Créez un compte d’entreprise avec le client précédemment créé en tant qu’administrateur de l’entreprise.
* Créez un produit simple (exemple : nom et **SKU** = TEST SIMPLE 1) qui n’est pas affecté à **Par défaut (Général)**.
* Demandez à l’administrateur de la société de demander un devis à l’aide du produit simple créé ci-dessus (exemple : TEST SIMPLE 1).

<u>Procédure à suivre</u>

1. Accédez au panneau d’administration Commerce.
1. Accédez à **Ventes > Devis**.
1. Ouvrez le **Devis**.
1. Cliquez sur le bouton **Ajouter un produit par SKU**.
1. Saisissez le **SKU** d’un autre produit (exemple : TEST SIMPLE 2) dans le champ de saisie **Saisir le SKU**.
1. Entrez une quantité valide dans le champ d&#39;entrée **Qté**.
1. Cliquez sur le bouton **Ajouter à la citation**.

<u>Résultats attendus</u>

* La grille **Produits non ajoutés au devis**, contenant le nom et le **SKU** du produit créé, s’affiche comme prévu.
* Une fois le produit configuré, l’administrateur peut l’ajouter au **devis** en cliquant sur le bouton **Ajouter des produits au devis**, comme prévu.

<u>Résultats réels</u>

* La grille **Produits non ajoutés au devis**, contenant le nom et le **SKU** du produit créé, n’apparaît pas.
* Le chargement de la page **Citation** est bloqué.

## Recommandation

Actuellement, il n’existe aucune solution à ce problème avec la modification des devis B2B, mais pour la gestion des commandes et des paniers, il est possible de sélectionner des produits dans la **Liste de produits** au lieu de les ajouter par **SKU**. Un correctif pour résoudre le problème sera disponible pour Adobe Commerce 2.4.1, dont la publication est prévue pour le 4e trimestre 2020.

## Lecture connexe

* [Problème connu d’Adobe Commerce 2.4.0 : l’actualisation des activités du client ne fonctionne pas](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problème connu d’Adobe Commerce 2.4.0 : les taux de taxe à l’exportation ne fonctionnent pas](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)

