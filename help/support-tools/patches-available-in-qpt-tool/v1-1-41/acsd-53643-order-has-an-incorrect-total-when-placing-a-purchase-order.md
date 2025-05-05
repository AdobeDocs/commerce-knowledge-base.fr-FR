---
title: "ACSD-53643 : le total de la commande est incorrect lors du placement d’une commande"
description: Appliquez le correctif ACSD-53643 pour résoudre le problème Adobe Commerce en raison duquel le total de la commande est incorrect lors du placement d’une commande avec des produits désactivés ou en rupture de stock.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643 : le total de la commande est incorrect lors du placement d’une commande

Le correctif ACSD-53643 corrige le problème en raison duquel la commande présente un total incorrect lors du placement d’une commande avec des produits désactivés ou en rupture de stock. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 est installé. L’ID de correctif est ACSD-53643. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le total de la commande est incorrect lors du placement d’une commande avec des produits désactivés ou en rupture de stock.

<u>Étapes à reproduire</u> :

1. Installez *[!UICONTROL B2B]* et *[!UICONTROL Inventory]*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** et définissez **[!UICONTROL Company]** = *Oui* et **[!UICONTROL Purchase Order]** = *Oui*.
1. Effacez le cache de configuration.
1. Créez une nouvelle société, activez-la et activez *[!UICONTROL Purchase order]* pour la société.
1. Créez un utilisateur pour la société.
1. Créez une *règle d&#39;approbation* pour approuver toutes les commandes de plus de *1 USD* par l&#39;administrateur de la société.
1. Créez une source supplémentaire.
1. Connectez-vous en tant que nouvel utilisateur de l’entreprise.
1. Ajoutez deux produits au panier et passez une commande.
1. Désactivez le second produit.
1. Connectez-vous en tant qu’administrateur de l’entreprise.
1. Ouvrez le bon de commande et vérifiez que le bon de commande contient les deux produits et que le total correspond aux deux produits.
1. Validez le bon de commande.
1. Placez la commande.
1. Ouvrez les détails de la commande.

<u>Résultats attendus</u> :

* Impossible de passer la commande même si un produit de la commande est *désactivé* ou *en rupture de stock*.
* Le bouton *[!UICONTROL Place Order]* est masqué.

<u>Résultats réels</u> :

La commande passée contient uniquement le premier produit actif, mais le total de la commande est calculé pour les deux produits.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
