---
title: "Adobe Commerce 2.4.2-p1 : note de facture avec une valeur incorrecte"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.2-p1, en raison duquel une note de facture avec une valeur incorrecte est générée lors de la modification du groupe de clients lors de la création de la commande. Ce problème est résolu dans la version 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1 : note de facture avec une valeur incorrecte

Cet article décrit un problème connu d’Adobe Commerce 2.4.2-p1, en raison duquel une note de facture avec une valeur incorrecte est générée lors de la modification du groupe de clients lors de la création de la commande. Ce problème est résolu dans la version 2.4.3.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.2-p1
* Adobe Commerce sur l’infrastructure cloud 2.4.2-p1

## Problème

Lorsque le groupe de clients est modifié au moment de la création de la commande, la facture est générée avec une note de facture incorrecte.

<u>Étapes à reproduire</u>:

1. Créez un **Tester le compte client** et ajoutez-le à la variable **Groupe de clients de vente au détail**.
1. Créez un **Nouvelle commande** pour le client test, ajoutez **Produit** et **Adresse**.
1. Sélectionner **Méthode d’expédition**.
1. Dans le **Informations du compte** , modifiez le groupe de clients à partir de **Détailleur** to **Gouvernement**.
1. Cliquez sur **Passer commande**.
1. Cliquez sur **Facture** > **Submit Invoice**.

<u>Résultats attendus</u>:

La remarque suivante devrait apparaître sous la rubrique **Notes de mise à jour de cette commande**  section : &quot;Facture de sommet envoyée avec succès. Montant : 0,00 $.&quot;

<u>Résultats réels</u>:

La remarque suivante s’affiche sous la section **Notes de mise à jour de cette commande** section : &quot;Facture de sommet envoyée avec succès. Montant : 3,23 $.&quot;

## Solution

Ce problème est résolu dans la version 2.4.3.
