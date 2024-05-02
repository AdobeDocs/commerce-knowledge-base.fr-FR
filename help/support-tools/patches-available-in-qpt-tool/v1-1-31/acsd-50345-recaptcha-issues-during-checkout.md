---
title: 'ACSD-50345 : problèmes reCAPTCHA lors du passage en caisse'
description: Appliquez le correctif ACSD-50345 pour résoudre le problème Adobe Commerce en raison duquel les validations reCAPTCHA v2 et v3 échouent lors du placement des commandes et du passage en caisse.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345 : problèmes reCAPTCHA lors du passage en caisse

Le correctif ACSD-50345 corrige le problème où les validations reCAPTCHA v2 et v3 échouent lors du placement de commandes et lors du passage en caisse. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.31 est installée. L’ID de correctif est ACSD-50345. Veuillez noter que le problème a été partiellement corrigé dans Adobe Commerce 2.4.6 et qu’il est prévu qu’il soit complètement corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**#1 de cas**

Google reCAPTCHA v2 ne se recharge pas après l’envoi d’un paiement en échec.

<u>Étapes à reproduire</u>

1. Configurer **[!UICONTROL Google reCAPTCHA v2]** (*Je ne suis pas un robot*).
1. Activez la variable **[!UICONTROL reCAPTCHA]** pour le paiement.
1. Essayez de passer une commande sans cliquer sur **[!UICONTROL reCAPTCHA]**.
1. Une fois que l’utilisateur reçoit le message d’erreur pour le reCAPTCHA manquant (*Échec de la validation de reCAPTCHA, veuillez réessayer.*), cliquez sur le bouton **[!UICONTROL reCAPTCHA]** et ensuite essayer de passer une commande.

<u>Résultats attendus</u>

La commande ne sera pas placée avec un reCAPTCHA incorrect.

<u>Résultats réels</u>

Une erreur est générée - *Échec de la validation de reCAPTCHA, veuillez réessayer.* et *Aucun panier de ce type avec id = 4*

**#2 de cas**

Google reCAPTCHA v3 Invisible ne fonctionne pas lors de l’extraction et la commande ne peut pas être placée. `PlaceOrder` n’est pas déclenché.

<u>Étapes à reproduire</u>

1. Configurez la variable **[!UICONTROL reCAPTCHA v3 Invisible]** de la **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Activer **[!UICONTROL reCAPTCHA v3 Invisible]** pour extraire ou placer une commande sous **[!UICONTROL Storefront]** .
1. Essayez de passer une commande avec la variable [!UICONTROL Check/Money order] mode de paiement.

<u>Résultats attendus</u>

La commande doit être placée avec la variable **[!UICONTROL reCAPTCHA]** activée.

<u>Résultats réels</u>

Après avoir cliqué sur le bouton **[!UICONTROL Place Order]** , il est désactivé, et rien ne se passe plus loin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
