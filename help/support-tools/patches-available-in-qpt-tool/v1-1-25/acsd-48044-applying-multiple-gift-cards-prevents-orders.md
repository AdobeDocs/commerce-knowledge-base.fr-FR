---
title: "ACSD-48044 : l’application de plusieurs cartes-cadeaux empêche l’envoi de commandes"
description: Appliquez le correctif ACSD-48044 pour résoudre le problème Adobe Commerce en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêche le placement des commandes.
exl-id: fe57063c-d69c-4b80-a59c-912c2603f6af
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044 : l’application de plusieurs cartes-cadeaux empêche le placement des commandes.

Le correctif ACSD-48044 corrige le problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêchait le placement des commandes. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 est installé. L’ID de correctif est ACSD-48044. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’application de plusieurs cartes-cadeaux à une seule commande avec livraison multiple empêche le placement des commandes.

<u>Étapes à reproduire</u> :

1. Installez une version propre d’Adobe Commerce.
1. Créez un produit simple au prix de 100 $ et un autre produit simple au prix de 10 $.
1. Connectez-vous à [!UICONTROL Admin panel] et créez deux cartes-cadeaux.

   * 02KB8M0H0GRD = 50 $
   * 00GXM6SUGBLW = 25 $

1. Créez un client avec deux adresses.
1. Ajoutez deux produits au panier.

   * Ajoutez d’abord le produit à 10 €, puis le produit à 100 €. Le problème ne peut pas être reproduit si le produit 100 $ est ajouté en premier.

1. Dans le panier, ajoutez les deux cartes-cadeaux que vous avez créées.
1. Cliquez sur **[!UICONTROL Ship to Multiple Addresses]** sur la page du panier.
1. Attribuez chaque produit à une adresse différente.
1. Accédez à la page **[!UICONTROL Shipping information]** .
1. Accédez à la page **[!UICONTROL Billing information]** .
1. Accédez à la page **[!UICONTROL Review Your Order]** où vous pouvez voir le problème.
1. Essayez de passer la commande.

<u>Résultats attendus</u> :

* Les cartes cadeau sont correctement appliquées au montant total.
* Les commandes sont passées.

<u>Résultats réels</u> :

Les montants des cartes-cadeaux sont mélangés avec une erreur *&quot;Veuillez corriger le code de carte-cadeau.&quot;* lors du placement de la commande.

* Premier produit :

   * Supprimer la carte cadeau (00GXM6SUGBLW) - 15,00 $
   * Supprimer la carte cadeau (02KB8M0H0GRD) - 0,00 $

* Deuxième produit :

   * Supprimer la carte cadeau (00GXM6SUGBLW) - 25 $
   * Supprimer la carte cadeau (02KB8M0H0GRD) - 35,00 $

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
