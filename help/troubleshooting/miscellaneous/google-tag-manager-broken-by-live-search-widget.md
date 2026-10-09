---
title: Le gestionnaire de balises Google est bloqué par le widget [!DNL Live Search]
description: Cet article propose une solution au [!DNL Live Search Product Listing Widget] qui provoque l’arrêt du fonctionnement de [!DNL Google Tag Manager].
feature: Install, Search, Best Practices
role: Admin, Developer
exl-id: 485f8ccb-cba2-4785-a8e1-a1e98c88b21e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%
---
# [!DNL Google Tag Manager] est rompu par le widget [!DNL Live Search]

Cet article propose une solution au [!DNL Live Search Product Listing Widget] qui provoque l’arrêt du fonctionnement de [!DNL Google Tag Manager].

## Produits et versions concernés

* Adobe Commerce version 2.4.4 - 2.4.6-p2

## Problème

La [!DNL Live Search Product Listing Widget] provoque l’arrêt du fonctionnement de [!DNL Google Tag Manager].

## Solution

Pour vous assurer que [!DNL Google Tag Manager] fonctionne avec [!DNL Live Search], utilisez l’*adaptateur de recherche*.

Pour ce faire, désactivez le widget dans l’interface d’administration. [!DNL Live Search] utilise ensuite par défaut l’*adaptateur de recherche*.

## Lecture connexe

* [[!DNL Live Search] Présentation du guide](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html?lang=fr) dans notre documentation sur Adobe Commerce Live Search

* [Installation [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=fr) dans notre documentation sur Adobe Commerce Live Search
