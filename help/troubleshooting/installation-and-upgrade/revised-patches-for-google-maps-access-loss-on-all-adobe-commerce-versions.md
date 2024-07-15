---
title: Correctifs révisés pour la perte d’accès aux cartes Google sur toutes les versions d’Adobe Commerce
description: "Cet article fournit un correctif pour les marchands Adobe Commerce qui ne sont compatibles avec aucune version récente de  [!DNL Google Maps] à partir de 3.54+."
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Correctifs modifiés pour la perte d’accès à [!DNL Google Maps] sur toutes les versions d’Adobe Commerce

Cet article fournit un correctif pour les marchands Adobe Commerce qui ne sont pas compatibles avec les versions [!DNL Google Maps] récentes de 3.54+. Ce correctif permet de résoudre le problème en raison duquel les marchands Adobe Commerce n’ont plus accès à [!DNL Google Maps] dans aucune version d’Adobe Commerce.

## Versions et produits concernés

* Versions d’Adobe Commerce et/ou d’autres technologies utilisées.
* Adobe Commerce *2.4.4* - *2.4.7* sur les versions cloud et On-Premise.

## Problème

Le *14 juin 2024* [!DNL Google Maps] version *3.53* a atteint la fin de vie et a été éteint par [!DNL Google].

Pour plus d&#39;informations, voir [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce n’était pas compatible avec les versions [!DNL  Google Maps] récentes de 3.54+.

L’incompatibilité a été provoquée par l’héritage `prototype.js script`, qui se charge via `lib/web/legacy-build.min.js` remplace la fonction native Array.from, ce qui entraîne un conflit direct avec l’API [!DNL  Google Maps].

Voir [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Étapes à reproduire</u> :

1. Cliquez sur **[!UICONTROL Content]** > **[!UICONTROL Pages]** et sélectionnez un **[!UICONTROL New Page]**.
1. Développez le bloc de contenu et cliquez sur le bouton Modifier **[!DNL PageBuilder]** .
1. Faites glisser le bloc de contenu Map du menu **[!DNL PageBuilder]** vers la page.

<u>Résultat attendu :</u>

[!DNL Google Maps] doit fonctionner comme prévu.

<u> Résultat réel : </u>

Lorsque vous déposez le bloc de contenu Map du menu **[!DNL PageBuilder]** vers la page, un message d’erreur tel que *&quot;Désolé ! Un problème s’est produit&quot;* s’affiche.

## Solution

* Tous les commerçants des versions de correctif 2.4.4, 2.4.5, 2.4.6 ou 2.4.7 doivent appliquer ces correctifs correspondants à leur version.

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

Ce problème sera corrigé définitivement dans le cadre des versions de correctifs propres à la sécurité d’août :
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Lecture connexe

[Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)