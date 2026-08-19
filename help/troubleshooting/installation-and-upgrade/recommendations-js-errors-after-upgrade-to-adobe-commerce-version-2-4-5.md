---
title: '[!UICONTROL Recommendations] [!DNL JS] erreurs après la mise à niveau vers Adobe Commerce version 2.4.5'
description: Cet article fournit un correctif pour le moment où, après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), il y a des erreurs dans la console  [!DNL JS]  liées aux modules de [!UICONTROL Recommendations] du produit.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '196'
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
