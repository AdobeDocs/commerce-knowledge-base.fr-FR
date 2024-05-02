---
title: 'ACSD-48694 : une erreur de demande de changement d’état non valide empêche le client de passer la commande'
description: Appliquez le correctif ACSD-48694 pour résoudre le problème Adobe Commerce où l’erreur *Changement d’état non valide demandé* empêche un client de passer une commande.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694 : *Changement d’état non valide demandé* empêche le client de passer la commande

Le correctif ACSD-48694 corrige le problème où l’erreur *Changement d’état non valide demandé* empêche un client de passer une commande. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.27 est installée. L’ID de correctif est ACSD-48694. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;erreur *Changement d’état non valide demandé* empêche un client de passer une commande.

<u>Étapes à reproduire</u>:

1. Ajoutez un léger délai lors de l’événement `/estimate-shipping-methods` en incluant une `sleep()` at `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` de la fonction `/estimate-shipping-methods` est terminée une fois que la `/shipping-information` lors du passage de l’étape d’expédition à l’étape de paiement lors du passage en caisse.
1. Configuration de la session à utiliser [!DNL Redis] avec la propriété *disable_locking: 1* .
1. Ouvrir **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** et activez *[!UICONTROL Persistent Shopping Cart]*.
1. Connectez-vous en tant que client et ajoutez un produit au panier.
1. Laissez la session du client expirer. Le cookie persistant et le panier persistent.
1. Maintenant, accédez à la page passage en caisse, ajoutez l’adresse de livraison et accédez à la section paiement .
1. Revenez à la page d’accueil ou à toute autre page et connectez-vous avec le compte client.
1. Laissez la session expirer à nouveau.
1. Accédez maintenant directement à la page de passage en caisse et accédez à l’étape de paiement.
1. Essayez de passer la commande.

<u>Résultats attendus</u>:

* Il n’y a pas d’erreur.
* La commande a été passée avec succès et une *Merci* s’affiche.

<u>Résultats réels</u>:

L&#39;erreur *Changement d’état non valide demandé* s’affiche, mais la commande est placée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
