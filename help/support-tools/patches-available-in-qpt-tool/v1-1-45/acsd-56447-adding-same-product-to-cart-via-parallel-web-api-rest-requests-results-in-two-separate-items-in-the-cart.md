---
title: "ACSD-56447 : l’ajout d’un même produit au panier via l’API REST web parallèle entraîne l’insertion de deux éléments distincts dans le panier"
description: Appliquez le correctif ACSD-56447 pour résoudre le problème Adobe Commerce en raison duquel l’ajout du même produit au panier via des demandes d’API REST web parallèles entraîne deux éléments distincts dans le panier.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447 : l’ajout d’un même produit au panier via l’API REST web parallèle entraîne l’apparition de deux éléments distincts dans le panier.

Le correctif ACSD-56447 corrige le problème en raison duquel l’ajout du même produit au panier via des demandes d’API REST web parallèles entraîne deux éléments distincts dans le panier. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.45 est installée. L’ID de correctif est ACSD-56447. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un même produit au panier via des demandes d’API REST web parallèles entraîne l’insertion de deux éléments distincts dans le panier.

<u>Étapes à reproduire</u>:

1. Générer un jeton client pour effectuer la demande d’appels API REST à l’aide de [!DNL Postman].
1. Créez un panier pour le client.
1. Utilisez le jeton généré ci-dessus pour créer un panier vide pour le client.
1. Utilisez CURL pour effectuer deux opérations `AddProductsToCart` requêtes s’exécutant en parallèle. Suivez les instructions de la section [Tutoriel sur le traitement des commandes](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) dans la documentation destinée aux développeurs.

<u>Résultats attendus</u>:

Les articles avec plusieurs quantités sont affichés sur une seule ligne.

<u>Résultats réels</u>:

Les mêmes SKU s’affichent sur plusieurs lignes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
