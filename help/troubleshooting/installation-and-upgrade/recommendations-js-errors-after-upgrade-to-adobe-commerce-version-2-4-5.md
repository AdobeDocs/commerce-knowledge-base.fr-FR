---
title: '[!UICONTROL Recommendations] des erreurs [!DNL JS] après la mise à niveau vers Adobe Commerce version 2.4.5'
description: Cet article fournit un correctif pour le moment où, après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), il y a des erreurs [!DNL JS] dans la console en rapport avec les modules de [!UICONTROL Recommendations] du produit.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%
---
# [!UICONTROL Recommendations] des erreurs [!DNL JS] après la mise à niveau vers Adobe Commerce version 2.4.5

Cet article fournit un correctif pour le moment où, après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), il y a des erreurs [!DNL JS] dans la console en rapport avec le produit [!UICONTROL Recommendations] les modules/unités.

Il n’est actuellement pas prévu de résoudre ce problème dans les versions ultérieures.

## Versions et produits concernés

* Adobe Commerce (toutes les méthodes de déploiement) lors de la mise à niveau vers la version 2.4.5

## Problème

Le problème est dû au fait que la page web du storefront fait toujours référence à certains modules/unités de [!UICONTROL Recommendations] de produit supprimés (blocs et/ou widgets) sur sa page d’accueil [!DNL CMS].

<u>Procédure à suivre </u> :

1. Mise à niveau vers Adobe Commerce 2.4.5.
1. Accédez à la page web du storefront.
1. Cliquez avec le bouton droit de la souris, puis sélectionnez **Inspect** pour ouvrir l&#39;inspecteur Web dans votre navigateur Web.
1. Cliquez sur l’onglet **[!UICONTROL Console]** .
1. Vérifiez les erreurs [!DNL JS].

<u>Résultats attendus</u> :

Mise à niveau réussie sans erreurs de [!DNL JS].

<u>Résultats réels</u> :

Plusieurs types différents d’erreurs [!DNL JS] s’affichent dans la console du navigateur web.

## Solution

Pour pallier ce problème, vous pouvez passer en revue toutes les unités de [!UICONTROL Recommendations] que vous avez utilisées sur la page et supprimer toutes les unités supprimées.
