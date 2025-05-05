---
title: '[!DNL Live Search] affiche les produits en rupture de stock, quels que soient les paramètres de statut du stock dans l’administrateur'
description: Cet article fournit des informations sur le problème connu où la page Liste des produits (PLP) affiche la mention *Nous ne pouvons pas trouver de produits correspondant à l’erreur de sélection* tandis que la fenêtre contextuelle de recherche renvoie certains éléments.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] affiche les produits en rupture de stock, quels que soient les paramètres de statut du stock dans l’administration

>[!IMPORTANT]
>
>Ce problème a été corrigé dans [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html?lang=fr). Pour installer la dernière version, reportez-vous à la section [Mise à jour [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=fr#update) du guide de l’utilisateur.

Cet article fournit des informations sur le problème connu où la page de liste de produits (PLP) affiche le *Nous ne pouvons pas trouver de produits correspondant à l’erreur de sélection* tandis que la fenêtre contextuelle de recherche renvoie certains éléments.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.x

## Problème

[!DNL Live Search] affiche les résultats de recherche, quels que soient les paramètres d’état du stock dans l’administrateur Adobe Commerce. Même lorsque le **[!UICONTROL Display Out-of-Stock Products]** est défini sur *Non*, les produits s’affichent. Cela entraîne l’erreur PLP *Nous ne pouvons pas trouver de produits correspondant à la sélection*.

<u>Étapes à reproduire</u> :

1. Créez une catégorie, ajoutez des produits. (Exemple : Catégorie = _Jeans_, Product1 = _Blue Jeans_, Product2 = _Black Jeans_)
1. Mettre hors stock tous les produits de la catégorie.
1. Définissez **[!UICONTROL Display Out-of-Stock Products]** sur *Non*.
1. Sur le storefront, saisissez *Jeans* dans le champ de recherche.
1. Cliquez sur **[!UICONTROL View All]** dans la fenêtre contextuelle.

<u>Résultat attendu</u> :

Vous voyez le message *Nous ne pouvons pas trouver de produits correspondant au message de sélection* sur PLP, et aucun produit ne s’affiche dans la fenêtre contextuelle de recherche.

<u>Résultat réel</u> :

Vous voyez le message *Nous ne pouvons pas trouver de produits correspondant au message de sélection* sur PLP, et les deux produits s’affichent dans la fenêtre contextuelle de recherche.

## Solution

Il n&#39;y a pas de solution à ce problème pour le moment. Notre équipe [!DNL Live Search] va bientôt fournir un paramètre pour configurer [!DNL Live Search] afin d’afficher correctement les produits.

## Lecture connexe

[Installez  [!DNL Live Search]](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/live-search/install) dans notre guide d’utilisation.
