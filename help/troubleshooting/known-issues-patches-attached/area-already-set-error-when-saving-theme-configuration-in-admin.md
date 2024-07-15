---
title: Erreur "Zone déjà définie" lors de l’enregistrement de la configuration du thème dans Admin
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.4 lié à l’obtention du message d’erreur *"La zone est déjà définie"* lors de la tentative de définition d’un thème pour la vue de magasin par défaut dans l’administrateur Commerce.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Erreur &quot;Zone déjà définie&quot; lors de l’enregistrement de la configuration du thème dans Admin

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.4 lié à l’obtention du message d’erreur &quot;La zone est déjà définie&quot;*lors de la tentative de définition d’un thème pour la vue de magasin par défaut dans l’administrateur Commerce.*

## Problème

Vous obtenez le message d’erreur &quot;*Une erreur s’est produite lors de l’enregistrement de cette configuration : la zone est déjà définie*&quot; lors de la tentative de définition d’un thème pour la vue de magasin par défaut.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Contenu** > **Conception** > **Configuration**.
1. Définissez la portée de configuration sur *Default Store View*.
1. Modifiez le thème dans la liste déroulante **Thème appliqué** . Par exemple, de *Luma* à *Vierge.*
1. Cliquez sur **Enregistrer la configuration**.

<u>Résultat attendu</u> : le thème sélectionné est appliqué pour la vue de magasin par défaut.

<u>Résultat réel</u> : le thème n’est pas appliqué, *&quot;Quelque chose s’est mal passé lors de l’enregistrement de cette configuration : la zone est déjà définie&quot;* le message d’erreur s’affiche.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, cliquez sur le lien suivant ou faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le fichier joint :

[Téléchargez MDVA-11106\_EE\_2.2.4\_v1.compositeur.patch.](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.4

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.0.X
* Adobe Commerce sur l’infrastructure cloud 2.1.X
* Adobe Commerce sur l’infrastructure cloud 2.2.0 - 2.2.5
* Adobe Commerce On-Premise 2.0.X
* Adobe Commerce On-Premise 2.1.X
* Adobe Commerce On-Premise 2.2.0 - 2.2.5

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Fichiers attachés
