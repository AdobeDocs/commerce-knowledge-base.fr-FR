---
title: Les clients de l’UE ne peuvent pas effectuer de paiements
description: Cet article fournit un correctif pour le problème des clients de l’Union européenne qui ne peuvent pas effectuer de paiements.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Les clients de l’UE ne peuvent pas effectuer de paiements

Cet article fournit un correctif pour le problème des clients de l’Union européenne qui ne peuvent pas effectuer de paiements.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions
* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problème

Les clients de l&#39;UE se plaignent du refus de leurs transactions de carte de crédit.

## Cause

L’Union européenne a révisé un règlement appelé Directive sur les services de paiement (PSD) avec une version mise à jour. [PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Il s’agit d’une directive de l’Union européenne (UE) qui vise à réglementer les services de paiement et les fournisseurs de services de paiement dans l’ensemble de l’UE et de l’Espace économique européen (EEE). Une authentification forte du client (SCA) est une exigence de PSD2 pour accroître la sécurité et l’authentification des données de paiement. Si vos solutions de paiement ne sont pas conformes aux exigences de la directive, il se peut que les clients ne puissent pas effectuer de paiements. Pour plus d’informations, voir [publication Adobe Commerce DevBlog associée](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Solution

Suivez les recommandations de la [Section Recommendations du fournisseur de paiement Adobe Commerce du blog de développement](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
