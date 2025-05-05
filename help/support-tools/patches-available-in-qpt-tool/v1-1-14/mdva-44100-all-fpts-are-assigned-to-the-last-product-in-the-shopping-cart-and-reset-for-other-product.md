---
title: "MDVA-44100 : tous les FPT sont affectés au dernier produit du panier"
description: Le correctif MDVA-44100 résout le problème en raison duquel tous les FPT sont affectés au dernier produit du panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-44100. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100 : tous les FPT sont affectés au dernier produit du panier.

Le correctif MDVA-44100 résout le problème en raison duquel tous les FPT sont affectés au dernier produit du panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-44100. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Tous les FPT sont affectés au dernier produit du panier et les valeurs FPT du reste des produits sont réinitialisées.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > **Configuration** > **Ventes** > **Taxe** et définissez :
   * Activer FPT = Oui
   * Appliquer la taxe à FPT = Oui
   * Inclure le FPT dans le sous-total = Oui
1. Accédez à **Magasins** > **Attribut** > **Produit**, puis créez un attribut avec type = Taxe fixe du produit.
1. Ajoutez l’attribut à un jeu d’attributs.
1. Créez deux produits à partir du jeu d’attributs et configurez l’attribut FPT pour votre pays et votre état.
1. Ajoutez les deux éléments à l’ordre.
1. Saisissez une adresse qui nécessite le paiement du FPT.
1. Placez la commande.
1. Vérifiez la liste des éléments dans l’ordre.

<u>Résultats attendus</u> :

Les FPT s’affichent sous chaque produit.

<u>Résultats réels</u> :

Les valeurs FPT des deux éléments s’affichent sous le deuxième élément.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
