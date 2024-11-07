---
title: "ACSD-46618 : le widget de liste de produits affiche des prix en cache incorrects pour le client connecté"
description: Appliquez un correctif pour résoudre le problème Adobe Commerce en raison duquel le widget de liste de produits affiche des prix en cache incorrects pour un client connecté.
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618 : le widget Liste de produits affiche des prix en cache incorrects pour un client connecté

Le correctif ACSD-46618 résout le problème en raison duquel le widget de liste de produits affiche des prix en cache incorrects pour un client connecté. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 est installé. L’ID de correctif est ACSD-46618. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif ACSD-46618 résout le problème en raison duquel le widget de liste de produits affiche des prix en cache incorrects pour un client connecté.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur Adobe Commerce, sélectionnez **[!UICONTROL Stores]**, puis **[!UICONTROL Configuration]**, développez **[!UICONTROL Sales]** et sélectionnez **[!UICONTROL Tax]**. Mettez à jour les paramètres de taxe pour afficher les prix, y compris et à l’exclusion des taxes.
1. Définissez **[!UICONTROL Enable Cross Border Trade]** = _Oui_.
1. Créez une règle fiscale qui ne s&#39;applique qu&#39;aux Etats-Unis.
1. Ajoutez un widget à la page d’accueil, y compris plusieurs produits.
1. Créez deux clients avec une adresse américaine et une adresse non américaine.
1. Connectez-vous à l’aide du client américain à partir du storefront. Assurez-vous que la page est mise en cache.
1. Observez le prix affiché dans le widget de page d’accueil.
1. Déconnectez-vous et connectez-vous à l’aide du client non américain.

<u>Résultats attendus</u> :

Le prix affiché dans le widget de la page d&#39;accueil correspond à l&#39;adresse du client.

<u>Résultats réels</u> :

Le widget de page d’accueil affiche les prix en utilisant la taxe pour les clients non américains.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
