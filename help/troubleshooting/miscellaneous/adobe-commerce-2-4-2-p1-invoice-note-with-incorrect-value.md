---
title: 'Adobe Commerce 2.4.2-p1 : note de facturation avec une valeur incorrecte'
description: Cet article décrit un problème Adobe Commerce 2.4.2-p1 connu où une note de facture avec une valeur incorrecte est générée lorsque le groupe de clients est modifié lors de la création de la commande. Ce problème est corrigé dans la version 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%
---
# Adobe Commerce 2.4.2-p1 : note de facturation avec une valeur incorrecte

Cet article décrit un problème Adobe Commerce 2.4.2-p1 connu où une note de facture avec une valeur incorrecte est générée lorsque le groupe de clients est modifié lors de la création de la commande. Ce problème est corrigé dans la version 2.4.3.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.2-p1
* Adobe Commerce sur l’infrastructure cloud 2.4.2-p1

## Problème

Lorsque le groupe de clients est modifié au moment de la création de la commande, la facture est générée avec une note de facture incorrecte.

<u>Procédure à suivre </u> :

1. Créez un **Compte client de test** et ajoutez-le au **Groupe de clients de vente au détail**.
1. Créez une **Nouvelle commande** pour le client ou la cliente de test, ajoutez **Produit** et **Adresse**.
1. Sélectionnez **Mode d’expédition**.
1. Dans la section **Informations sur le compte**, remplacez le groupe de clients **Retailer** par **Gouvernement**.
1. Cliquez sur **Passer une commande**.
1. Cliquez sur **Facture** > **Soumettre la facture**.

<u>Résultats attendus</u> :

La note suivante doit apparaître sous la section **Notes de cette commande** : « Facture Vertex envoyée avec succès. Montant : 0,00 $

<u>Résultats réels</u> :

La note suivante apparaît sous la section **Notes de cette commande** : « Facture Vertex envoyée avec succès. Montant : 3,23 $. »

## Solution

Ce problème est corrigé dans la version 2.4.3.
