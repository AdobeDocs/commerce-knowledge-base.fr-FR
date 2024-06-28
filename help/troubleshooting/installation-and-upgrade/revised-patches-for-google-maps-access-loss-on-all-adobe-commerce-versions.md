---
title: Correctifs révisés pour la perte d’accès aux cartes Google sur toutes les versions d’Adobe Commerce
description: '"Cet article fournit un correctif pour les marchands Adobe Commerce qui ne sont pas compatibles avec les [!DNL Google Maps] versions 3.54+.'''
feature: Install, Upgrade
role: Developer
source-git-commit: 575fce2f678321ff184779895d43be90828c2ce4
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Correctifs révisés pour [!DNL Google Maps] perte d’accès sur toutes les versions d’Adobe Commerce

Cet article fournit un correctif pour les marchands Adobe Commerce qui ne sont pas compatibles avec les [!DNL Google Maps] versions 3.54+. Ce correctif permet de résoudre le problème en raison duquel les marchands Adobe Commerce n’ont pas accès à [!DNL Google Maps] dans n’importe quelle version d’Adobe Commerce.

## Versions et produits concernés

* Versions d’Adobe Commerce et/ou d’autres technologies utilisées.
* Adobe Commerce *2.4.4* - *2.4.7* sur les versions cloud et On-Premise.

## Problème

Activé *14 juin 2024* [!DNL Google Maps] version *3,53* a atteint la fin de la vie et a été éteint par [!DNL Google].

[Pour plus d’informations, voir ([!DNL Google Maps Platform: Maps JavaScript API])] (https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce n’était pas compatible avec les [!DNL  Google Maps] versions 3.54+.

L’incompatibilité était due à l’héritage `prototype.js script`, qui a été chargé par `lib/web/legacy-build.min.js` remplace la fonction native Array.from, ce qui entraîne un conflit direct avec [!DNL  Google Maps] API.

[Voir à ce propos la section[!DNL Google Maps: JS Best Practices])] (https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Étapes à reproduire</u> :

1. Cliquez sur **[!UICONTROL Content]** > **[!UICONTROL Pages]** > et sélectionnez un **[!UICONTROL New Page]**.
1. Développez le bloc de contenu et cliquez sur Modifier . **[!DNL PageBuilder]** bouton .
1. Faites glisser le bloc de contenu de la zone Mapper depuis le **[!DNL PageBuilder]** du menu à la page.

<u>Résultat attendu :</u>

[!DNL Google Maps] doit fonctionner comme prévu.

<u> Résultat réel :</u>

Lorsque vous faites glisser le bloc de contenu Mapper depuis **[!DNL PageBuilder]** sur la page, un message d’erreur tel que *&quot;Désolé ! Quelque chose s&#39;est mal passé&quot;* s’affiche.

## Solution

* Tous les commerçants des versions de correctif 2.4.4, 2.4.5, 2.4.6 ou 2.2.7 doivent appliquer ces correctifs correspondants à leur version.

## Correctif

Utilisez les correctifs ci-joints suivants, en fonction de la version d’Adobe Commerce :

**Pour les versions 2.4.4 :**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_compositeur.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Pour les versions 2.4.5 :**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_compositeur.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Pour les versions 2.4.6 :**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_compositeur.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Pour les versions 2.4.7 :**
[ACSD-60245_Google_maps_API_2.4.7_compositeur.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Veuillez noter**

Ce problème sera corrigé de manière permanente dans les versions de correctifs de sécurité uniquement d’août : 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10.

## Lecture connexe

[Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)