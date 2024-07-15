---
title: '[!UICONTROL Recommendations] [!DNL JS] Erreurs après la mise à niveau vers Adobe Commerce version 2.4.5'
description: Cet article fournit un correctif pour les erreurs survenant après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), survenant dans la console des erreurs liées aux modules [!UICONTROL Recommendations] du produit. [!DNL JS]
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] erreurs après la mise à niveau vers Adobe Commerce version 2.4.5

Cet article fournit un correctif pour le cas où, après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), des erreurs [!DNL JS] se produisent dans la console en rapport avec les modules/unités du produit [!UICONTROL Recommendations].

Il n’est actuellement pas prévu de résoudre ce problème dans les versions futures.

## Versions et produits concernés

* Adobe Commerce (toutes les méthodes de déploiement) lors de la mise à niveau vers la version 2.4.5

## Problème

Le problème est dû à la page web storefront qui fait toujours référence à certains modules/unités de produit [!UICONTROL Recommendations] supprimés (blocs et/ou widgets) sur sa page d’accueil [!DNL CMS].

<u>Étapes à reproduire</u> :

1. Mise à niveau vers Adobe Commerce 2.4.5.
1. Accédez à la page web storefront.
1. Cliquez avec le bouton droit de la souris, puis sélectionnez **Inspect** pour ouvrir l’Inspecteur Web sur votre navigateur Web.
1. Cliquez sur l’onglet **[!UICONTROL Console]** .
1. Vérifiez les erreurs [!DNL JS].

<u>Résultats attendus</u> :

Mise à niveau réussie sans erreur [!DNL JS].

<u>Résultats réels</u> :

Plusieurs types d’erreurs [!DNL JS] s’affichent dans la console du navigateur web.

## Solution

Pour pallier ce problème, vous pouvez passer en revue toutes les unités [!UICONTROL Recommendations] que vous avez utilisées sur la page et supprimer toutes les unités supprimées.
