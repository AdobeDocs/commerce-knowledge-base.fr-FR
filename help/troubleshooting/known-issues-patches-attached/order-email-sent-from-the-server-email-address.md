---
title: Commande d’email envoyée à partir de l’adresse email du serveur
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.4 lié aux courriers électroniques de commande envoyés à partir de l’adresse électronique du serveur.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Commande d’email envoyée à partir de l’adresse email du serveur

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.4 lié aux courriers électroniques de commande envoyés à partir de l’adresse électronique du serveur.

## Problème

Les emails de confirmation de commande sont envoyés à partir de l’adresse email du serveur Apache. D’autres emails (mot de passe oublié, etc.) sont envoyés à partir des adresses email configurées.

<u>Étapes à reproduire</u>:

1. Placez une commande à l’aide de la fonction **Envoyer la confirmation de commande** case cochée.
1. Vérifier l&#39;email.

<u>Résultat attendu</u>:

L&#39;email a été envoyé à partir de l&#39;adresse d&#39;envoi configurée par Adobe Commerce.

<u>Résultat réel</u>:

L&#39;email a été envoyé à partir de l&#39;adresse email configurée dans le serveur Apache en cours d&#39;utilisation.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-10993\_EE\_2.2.4\_v1.compositeur.patch.](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.4

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.5
* Adobe Commerce sur l’infrastructure cloud 2.2.6
* Adobe Commerce on Cloud infrastructure 2.2.7
* Adobe Commerce sur l’infrastructure cloud 2.2.8
* Adobe Commerce on-premise 2.2.4
* Adobe Commerce On-Premise 2.2.5
* Adobe Commerce on-premise 2.2.6
* Adobe Commerce On-Premise 2.2.7
* Adobe Commerce On-Premise 2.2.8
* Adobe Commerce on-premise 2.3.0

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Fichiers attachés
