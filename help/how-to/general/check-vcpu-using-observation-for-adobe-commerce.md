---
title: Affichage du niveau de processeur virtuel de l’environnement dans votre cluster sur Adobe Commerce
promoted: true
description: Cet article explique comment vérifier l’allocation de niveau processeur virtuel à l’aide de l’onglet Infra New Relic dans Observation pour Adobe Commerce. L’observation pour Adobe Commerce est une applet de commande New Relic qui indique l’état de votre site Adobe Commerce, les vues actuelles et passées.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: ffb7b597d38eaed4b66e23ea533c275746e7181a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%
---
# Affichage du niveau de processeur virtuel de l’environnement dans votre cluster sur Adobe Commerce

Cet article explique comment vérifier l’allocation de niveau processeur virtuel à l’aide de l’onglet Infra New Relic dans Observation pour Adobe Commerce. L’observation pour Adobe Commerce est une applet de commande New Relic qui indique l’état de votre site Adobe Commerce, les vues actuelles et passées.

## Produits et versions concernés :

Adobe Commerce sur les infrastructures cloud 2.4.3 à 2.4.6

## Vérifiez l’affectation de niveau processeur virtuel avec l’observation pour Adobe Commerce :

Pour accéder à l’applet de commande New Relic Observation for Adobe Commerce et vous connecter, procédez comme suit :

1. Sur la page d’accueil de New Relic, cliquez sur **Applications**.
1. Cliquez sur **Observation pour Adobe Commerce**.
1. L’applet de commande Observation pour Adobe Commerce s’ouvre.
1. Cliquez sur le menu déroulant **Sélectionner un compte** et sélectionnez un compte.
1. Vous pouvez renseigner l’identifiant du projet, le numéro ou le nom du compte New Relic ou parcourir la liste des comptes.
1. Cliquez sur le menu déroulant bleu clair avec l’icône d’horloge (vers le haut à droite de la fenêtre de l’aiguille).
1. Si vous essayez d’identifier la cause d’un événement/problème, sélectionnez une heure antérieure à la date et à l’heure du ticket pour voir s’il y a eu des événements/données précédents. Vous pouvez utiliser les périodes prédéfinies ou définir une période personnalisée en sélectionnant **Définir personnalisé**.
1. Dans les onglets, cliquez sur **Infra**. Il existe trois graphiques de niveau processeur virtuel :
   * Le premier graphique affiche la vue **niveau processeur virtuel sur la chronologie SUPÉRIEURE à 2 semaines (vous devrez sélectionner une chronologie SUPÉRIEURE à 2 semaines). REMARQUE : le taux d’échantillonnage sera de par jour. Si des uptailles/downtailles de cluster se produisent un jour, la taille de niveau de fin s’affiche le jour suivant**.
   * Le deuxième graphique présente la vue **niveau processeur virtuel sur la chronologie (vous devez sélectionner une chronologie SUPÉRIEURE à 24 heures, mais non supérieure à 2 semaines)**.
   * Le troisième graphique présente la vue de niveau **vCPU sur la chronologie PAR NOEUD, doit afficher la chronologie INFÉRIEURE à 24 heures**.
