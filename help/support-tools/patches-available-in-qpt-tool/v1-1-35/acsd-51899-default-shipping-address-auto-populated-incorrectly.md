---
title: 'ACSD-51899 : l’adresse de livraison par défaut n’est pas renseignée correctement'
description: Appliquez le correctif ACSD-51899 pour résoudre le problème Adobe Commerce en raison duquel l’adresse de livraison par défaut est automatiquement renseignée avec une adresse incorrecte.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899 : l’adresse de livraison par défaut est renseignée automatiquement de manière incorrecte

Le correctif ACSD-51899 corrige le problème en raison duquel l’adresse de livraison par défaut est automatiquement renseignée avec une adresse incorrecte. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-51899. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’adresse de livraison par défaut est automatiquement renseignée avec une adresse incorrecte.

<u>Étapes à reproduire</u>:

1. Activer **Sélecteur en magasin** sous la méthode d’expédition.
1. Créer *stock* et *source*.
1. Créez un produit et affectez-le à la source.
1. Ajoutez un produit au panier.
1. Cliquez sur **Passez à l’extraction** de mini-panier.
1. Saisissez l’adresse électronique de test et sélectionnez **Sélectionner en magasin**.
1. Cliquez sur le bouton **Sélectionner un magasin** et sélectionnez l’emplacement de votre choix.
1. Cliquez sur le bouton **next** bouton .
1. Accédez au **Page d’accueil** en cliquant sur le logo de la boutique.
1. Ouvrez le **Mini panier**.
1. Cliquez sur le lien hypertexte inférieur nommé **Afficher et modifier le panier**.
1. Cliquez sur **Passez à l’extraction**.
1. Cliquez sur le bouton d’expédition dans la page d’expédition.

<u>Résultats attendus</u>

Le champ Adresse de livraison reste vide, à l’exception de *Pays, région et code postal*.

<u>Résultats réels</u>

L’adresse de livraison par défaut est automatiquement renseignée par *Saut en magasin* après avoir actualisé la page.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
