---
title: Correctifs révisés pour la perte d’accès aux cartes Google sur toutes les versions d’Adobe Commerce
description: Cet article fournit un correctif pour les commerçants Adobe Commerce qui ne sont compatibles avec aucune version [!DNL Google Maps] récente à partir de la version 3.54+.
feature: Install, Upgrade
role: Developer
exl-id: 6151e89a-3190-40cb-b599-94ae5530488b
source-git-commit: d7e58d6a9ed8e9b369ea41165cbdd6b362e40824
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%
---
# Correctifs révisés pour la perte d’accès [!DNL Google Maps] sur toutes les versions d’Adobe Commerce

Cet article fournit un correctif pour les commerçants Adobe Commerce qui ne sont compatibles avec aucune version [!DNL Google Maps] récente à partir de la version 3.54+. Ce correctif permet de résoudre le problème au cours duquel les commerçants Adobe Commerce n’ont plus accès aux [!DNL Google Maps] dans aucune version d’Adobe Commerce.

## Versions et produits concernés

* Versions d’Adobe Commerce et/ou d’autres technologies utilisées.
* Adobe Commerce *2.4.4* - *2.4.7* sur les versions cloud et on-premise.

## Problème

Le *14 juin 2024* [!DNL Google Maps] version *3.53* a atteint sa fin de vie et a été arrêtée par [!DNL Google].

Pour plus d’informations, voir [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce n’était compatible avec aucune version [!DNL  Google Maps] récente à partir de la version 3.54+.

L’incompatibilité était due à l’`prototype.js script` hérité, qui était chargé via `lib/web/legacy-build.min.js` remplace la fonction native Array.from, ce qui entraîne un conflit direct avec l’API [!DNL  Google Maps].

Pour plus d&#39;informations, consultez la section [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Procédure à suivre </u> :

1. Cliquez sur **[!UICONTROL Content]** > **[!UICONTROL Pages]** > et sélectionnez un **[!UICONTROL New Page]**.
1. Développez le Bloc de contenu et cliquez sur le bouton Modifier le **[!DNL PageBuilder]** .
1. Faites glisser le bloc de contenu Map du menu **[!DNL PageBuilder]** vers la page.

<u>Résultat attendu : </u>

[!DNL Google Maps] doit fonctionner comme prévu.

<u> résultat réel : </u>

Lorsque vous déposez le bloc de contenu Mapper **[!DNL PageBuilder]** menu vers la page, un message d’erreur tel que *« Désolé ! Un problème s’est produit »* s’affiche.

## Solution

* Tous les commerçants de toute version de correctif 2.4.4, 2.4.5, 2.4.6 ou 2.4.7 doivent appliquer ces correctifs correspondants à leur version.

## Patch

Utilisez les correctifs ci-joints, en fonction de la version d’Adobe Commerce :

**Pour les versions 2.4.4 :**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Pour les versions 2.4.5 :**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Pour les versions 2.4.6 :**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Pour les versions 2.4.7 :**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Remarque**

Ce problème sera définitivement résolu dans le cadre des versions de correctifs d’août pour la sécurité uniquement :
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Lectures connexes

[Application d’un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)
