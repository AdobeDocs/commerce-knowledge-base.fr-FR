---
title: Affichage du niveau vCPU de l’environnement dans votre grappe sur Adobe Commerce
promoted: true
description: Cet article explique comment vérifier l’allocation de niveau vCPU à l’aide de l’onglet infrarouge New Relic sur Observation pour Adobe Commerce. L’observation pour Adobe Commerce est un point-virgule New Relic qui indique l’état de votre site Adobe Commerce, les vues d’heure actuelle et passées.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Affichage du niveau vCPU de l’environnement dans votre grappe sur Adobe Commerce

Cet article explique comment vérifier l’allocation de niveau vCPU à l’aide de l’onglet infrarouge New Relic sur Observation pour Adobe Commerce. L’observation pour Adobe Commerce est un point-virgule New Relic qui indique l’état de votre site Adobe Commerce, les vues d’heure actuelle et passées.

## Produits et versions concernés :

Adobe Commerce sur l’infrastructure cloud 2.4.3 - 2.4.6

## Vérifiez l’allocation du niveau vCPU avec Observation pour Adobe Commerce :

Pour accéder à l’horodatage d’observation New Relic pour Adobe Commerce et vous connecter :

1. Sur la page d’accueil de New Relic, cliquez sur **Applications**.
1. Cliquez sur **Observation pour Adobe Commerce**.
1. Le point d’entrée Observation pour Adobe Commerce s’ouvre.
1. Cliquez sur la liste déroulante **Sélectionner un compte** et sélectionnez un compte.
1. Vous pouvez renseigner l’ID de projet, le numéro de compte ou le nom du compte New Relic, ou parcourir la liste des comptes.
1. Cliquez sur le menu déroulant bleu clair avec l’icône d’horloge (en haut à droite de la fenêtre du sélecteur de couches).
1. Si vous essayez d’identifier la cause d’un événement/problème, sélectionnez une heure avant la date et l’heure du ticket pour voir s’il y avait eu des événements/données précédents. Vous pouvez utiliser les périodes prédéfinies ou définir une période personnalisée en sélectionnant **Définir personnalisé**.
1. Sur les onglets, cliquez sur **infrara**. Il existe trois graphiques de niveau vCPU :
   * Le premier graphique affiche une **vue de niveau CPU sur une chronologie SUPÉRIEURE 2 semaines (vous devez sélectionner une chronologie SUPÉRIEURE À 2 semaines). REMARQUE : Le taux d’échantillonnage sera par jour. Si des mises à niveau/réductions de cluster se produisent un jour, la taille du niveau de fin s’affiche le jour suivant**.
   * Le deuxième graphique affiche la **vue de niveau processeur sur la chronologie (nécessité de sélectionner une chronologie SUPÉRIEURE à 24 heures mais pas supérieure à 2 semaines)**.
   * Le troisième graphique montre la vue de niveau **vCPU sur la chronologie PAR NODE, doit examiner la chronologie MOINS de 24 heures**.

## Lecture connexe

* [Présentation de l’observation pour Adobe Commerce](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) dans notre base de connaissances d’assistance.
