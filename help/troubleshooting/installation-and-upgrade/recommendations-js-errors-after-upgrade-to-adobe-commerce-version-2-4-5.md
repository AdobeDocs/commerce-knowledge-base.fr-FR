---
title: '''[!UICONTROL Recommendations] [!DNL JS] Erreurs après la mise à niveau vers Adobe Commerce version 2.4.5"'
description: Cet article fournit un correctif pour le cas où, après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), il existe des [!DNL JS] erreurs dans la console liées au produit [!UICONTROL Recommendations] modules.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] erreurs après la mise à niveau vers Adobe Commerce version 2.4.5

Cet article fournit un correctif pour le cas où, après la mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement), il existe des [!DNL JS] erreurs dans la console liées au produit [!UICONTROL Recommendations] modules/unités.

Il n’est actuellement pas prévu de résoudre ce problème dans les versions futures.

## Versions et produits concernés

* Adobe Commerce (toutes les méthodes de déploiement) lors de la mise à niveau vers la version 2.4.5

## Problème

Le problème est dû au fait que la page web storefront fait toujours référence à un produit supprimé. [!UICONTROL Recommendations] modules/unités (blocs et/ou widgets) sur sa page d’accueil [!DNL CMS].

<u>Étapes à reproduire</u>:

1. Mise à niveau vers Adobe Commerce 2.4.5.
1. Accédez à la page web storefront.
1. Cliquez avec le bouton droit de la souris, puis sélectionnez **Inspect** pour ouvrir l’Inspecteur web dans votre navigateur web.
1. Cliquez sur le bouton **[!UICONTROL Console]** .
1. Consultez la section [!DNL JS] erreurs.

<u>Résultats attendus</u>:

Mise à niveau réussie sans [!DNL JS] erreurs.

<u>Résultats réels</u>:

Plusieurs types différents [!DNL JS] les erreurs s’affichent dans la console du navigateur web.

## Solution

Pour pallier ce problème, vous pouvez consulter toutes les [!UICONTROL Recommendations] unités que vous avez utilisées sur la page et supprimez les unités supprimées.
