---
title: "Adobe Commerce 2.4.1 : page vide lors de l’enregistrement du formulaire Digital Page Builder"
description: Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.1 pour l’affichage d’une page web vide après l’enregistrement d’un formulaire du Créateur de pages dotdigital dans le panneau d’administration lors de l’utilisation du navigateur Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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
1. Accédez à **Contenu** et cliquez sur le bouton **Modifier avec le générateur de pages** bouton .
1. Faites glisser le **formulaire dotdigital** block et select **Modifier**.
1. Sélectionnez l’un des formulaires de test, puis choisissez **Incorporer** et enregistrez le formulaire.
1. Enregistrez la modification de la page.

<u>Résultat attendu :</u>

La page web doit être enregistrée avec succès.

<u>Résultat réel :</u>

La page web est vide. Après le rechargement de la page web, les modifications sont appliquées.

## Solution

La solution consiste à utiliser un autre navigateur que Safari. Le problème devrait être résolu dans la prochaine version d’Adobe Commerce 2.4.2 au 1er trimestre 2021.

## Lecture connexe

* [Qu’est-ce que le créateur de pages ?](https://devdocs.magento.com/page-builder/docs/) dans notre documentation destinée aux développeurs.
* [Configuration du créateur de pages](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) dans notre documentation destinée aux développeurs.
* [Page Builder](https://docs.magento.com/user-guide/cms/page-builder.html) dans notre guide d’utilisation.
* [Créateur de pages - Éléments](https://docs.magento.com/user-guide/cms/page-builder-elements.html) dans notre guide d’utilisation.
