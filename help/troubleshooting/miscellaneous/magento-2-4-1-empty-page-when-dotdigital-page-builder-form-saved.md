---
title: "Adobe Commerce 2.4.1 : page vide lors de l’enregistrement du formulaire Digital Page Builder"
description: Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.1 pour l’affichage d’une page web vide après l’enregistrement d’un formulaire du Créateur de pages dotdigital dans le panneau d’administration lors de l’utilisation du navigateur Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 : page vide lors de l’enregistrement du formulaire Digital Page Builder

Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.1 pour l’affichage d’une page web vide après l’enregistrement d’un formulaire du Créateur de pages dotdigital dans le panneau d’administration lors de l’utilisation du navigateur Safari.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.1
* Adobe Commerce sur l’infrastructure cloud 2.4.1

## Problème

<u>Étapes à reproduire</u>

1. Accédez à **Panneau d’administration** > **Contenu** > **Pages**, puis sélectionnez **Modifier** de n’importe quelle page.
1. Accédez à **Contenu** et cliquez sur le bouton **Modifier avec le générateur de pages** .
1. Faites glisser le bloc **dotdigital form** et sélectionnez **Edit**.
1. Sélectionnez l’un des formulaires de test, puis le mode **Incorporé** et enregistrez le formulaire.
1. Enregistrez la modification de la page.

<u>Résultat attendu :</u>

La page web doit être enregistrée avec succès.

<u>Résultat réel :</u>

La page web est vide. Après le rechargement de la page web, les modifications sont appliquées.

## Solution

La solution consiste à utiliser un autre navigateur que Safari. Le problème devrait être résolu dans la prochaine version d’Adobe Commerce 2.4.2 au 1er trimestre 2021.

## Lecture connexe

* [Qu’est-ce que le créateur de pages ?](https://developer.adobe.com/commerce/frontend-core/page-builder/) dans notre documentation destinée aux développeurs.
* [Configuration du créateur de pages](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=fr) dans notre documentation destinée aux développeurs.
* [Page Builder](https://experienceleague.adobe.com/fr/docs/commerce-admin/page-builder/introduction) dans notre guide d’utilisation.
* [Page Builder - Elements](https://experienceleague.adobe.com/fr/docs/commerce-admin/page-builder/workspace#elements) dans notre guide d’utilisation.
