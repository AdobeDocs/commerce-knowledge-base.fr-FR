---
title: 'Adobe Commerce 2.4.1 : page vide lorsque le formulaire dotdigital Page Builder est enregistré'
description: Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.1 pour afficher une page web vide après l’enregistrement d’un formulaire Page Builder numérique dans le panneau d’administration lors de l’utilisation du navigateur Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%
---
# Adobe Commerce 2.4.1 : page vide lorsque le formulaire dotdigital Page Builder est enregistré

Cet article fournit une solution à un problème connu dans Adobe Commerce 2.4.1 pour afficher une page web vide après l’enregistrement d’un formulaire Page Builder numérique dans le panneau d’administration lors de l’utilisation du navigateur Safari.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.1
* Adobe Commerce sur les infrastructures cloud 2.4.1

## Problème

<u>Procédure à suivre</u>

1. Accédez à **Panneau d’administration** > **Contenu** > **Pages**, puis sélectionnez **Modifier** sur n’importe quelle page.
1. Accédez à **Contenu** et cliquez sur le bouton **Modifier avec Page Builder**.
1. Faites glisser le bloc **dotdigital form** et sélectionnez **Modifier**.
1. Sélectionnez l’un des formulaires de test, puis choisissez le mode **Incorporé** et enregistrez le formulaire.
1. Enregistrez la modification de page.

<u>Résultat attendu : </u>

La page web doit être enregistrée avec succès.

<u>Résultat réel :</u>

La page web est vide. Une fois la page web rechargée, les modifications sont appliquées.

## Solution

La solution consiste à utiliser un autre navigateur que Safari. Le problème devrait être corrigé dans la prochaine version, Adobe Commerce 2.4.2, au 1er trimestre 2021.

## Lecture connexe

* [Qu’est-ce que Page Builder &#x200B;](https://developer.adobe.com/commerce/frontend-core/page-builder/) dans la documentation destinée aux développeurs.
* [Configuration de Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) dans notre documentation destinée aux développeurs.
* [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/introduction) dans notre guide de l’utilisateur.
* [Page Builder - Éléments](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/workspace#elements) dans notre guide de l’utilisateur.
