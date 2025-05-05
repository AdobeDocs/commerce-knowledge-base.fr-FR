---
title: '"ACSD-52606 : message d’erreur affiché lorsque l’utilisateur clique sur "Avertir que la commande est prête pour la récupération"'
description: Appliquez le correctif ACSD-52606 pour résoudre le problème Adobe Commerce où un message d’erreur s’affiche lorsque l’utilisateur clique sur **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606 : message d’erreur affiché lorsque l’utilisateur clique sur &quot;Avertir la commande est prête pour la récupération&quot;.

Le correctif ACSD-52606 corrige le problème en raison duquel un message d’erreur *Votre commande n’est pas prête pour la récupération* s’affiche lorsque l’utilisateur clique sur **[!UICONTROL Notify Order is Ready for Pickup]**. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.37 est installé. L’ID de correctif est ACSD-52606. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message d’erreur *Votre commande n’est pas prête pour la récupération* s’affiche à l’écran lorsque l’utilisateur clique sur **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Conditions préalables</u> :

Les modules d’inventaire sont installés.

<u>Étapes à reproduire</u> :

1. Installez une nouvelle instance.
1. Créez une nouvelle source et un nouveau stock.
1. Affectez la nouvelle source au site web par défaut.
1. Activez l’emplacement de sélection de la source nouvellement créée.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** et activez **[!UICONTROL In-Store Delivery]**.
1. Créez un produit simple *In Stock* avec *QTY=0* pour tous les stocks et *[!UICONTROL Manage Stock = No]* et affectez-le aux deux sources.
1. Créez une commande à partir de l’interface avec le produit créé à l’étape précédente, en choisissant *[!UICONTROL In-Store Pickup]* comme méthode de livraison.
1. Dans Admin, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Cliquez sur **[!UICONTROL Notify order is ready for pickup]**.

<u>Résultats attendus</u> :

Vous êtes averti sans erreur.

<u>Résultats réels</u> :

Vous recevez le message d’erreur suivant : *Votre commande n’est pas prête pour le nettoyage*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
