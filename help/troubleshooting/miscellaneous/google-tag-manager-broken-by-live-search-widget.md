---
title: Le Gestionnaire de balises de Google est rompu par le widget  [!DNL Live Search]
description: Cet article offre une solution au  [!DNL Live Search Product Listing Widget] problème entraînant l’arrêt du fonctionnement de  [!DNL Google Tag Manager] .
feature: Install, Search, Best Practices
role: Admin, Developer
exl-id: 485f8ccb-cba2-4785-a8e1-a1e98c88b21e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# [!DNL Google Tag Manager] est rompu par le widget [!DNL Live Search]

Cet article offre une solution au [!DNL Live Search Product Listing Widget] qui empêche [!DNL Google Tag Manager] de fonctionner.

## Produits et versions concernés

* Adobe Commerce version 2.4.4 - 2.4.6-p2

## Problème

[!DNL Live Search Product Listing Widget] entraîne l’arrêt du fonctionnement de [!DNL Google Tag Manager].

## Solution

Pour vous assurer que [!DNL Google Tag Manager] fonctionne avec [!DNL Live Search], utilisez l’ *adaptateur de recherche*.

Pour ce faire, désactivez le widget dans Admin. [!DNL Live Search] utilise ensuite par défaut l’ *adaptateur de recherche*.

## Lecture connexe

* [[!DNL Live Search] Présentation du guide](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html) dans notre documentation Adobe Commerce Live Search

* [Installation [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) dans notre documentation Adobe Commerce Live Search
