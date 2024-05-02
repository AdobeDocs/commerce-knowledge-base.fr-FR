---
title: '''ACSD-47232 : le coupon n''est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché'''
description: Appliquez le correctif ACSD-47232 pour résoudre le problème Adobe Commerce où le coupon n’est pas appliqué lorsque [!UICONTROL Same as Billing Address] est cochée.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232 : le coupon n&#39;est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché

Le correctif ACSD-47232 corrige le problème en raison duquel le coupon n’est pas appliqué lorsque **[!UICONTROL Same as Billing Address]** est cochée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.23 est installée. L’ID de correctif est ACSD-47232. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le bon n’est pas appliqué lorsque **[!UICONTROL Same as Billing Address]** est cochée.

<u>Étapes à reproduire</u>:

1. Installez Adobe Commerce.
1. Créer un produit simple avec du poids = *8*.
1. Créez un client avec l’adresse de facturation et de livraison par défaut.
1. Créez une règle de prix de panier avec un coupon.
   * Dans **[!UICONTROL Conditions]** sections, ajout *Poids total égal ou supérieur à 5*
1. Essayez de créer une nouvelle commande dans le [!UICONTROL Commerce] Administrateur.
   * Utilisez le client créé tout à l’heure
   * Ajout d’un produit
   * Essayer d&#39;appliquer le coupon

<u>Résultats attendus</u>:

Le coupon est appliqué.

<u>Résultats réels</u>:

Vous obtenez une erreur similaire à celle-ci : *Le code de coupon 123 n&#39;est pas valide. Vérifiez le code, puis réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
