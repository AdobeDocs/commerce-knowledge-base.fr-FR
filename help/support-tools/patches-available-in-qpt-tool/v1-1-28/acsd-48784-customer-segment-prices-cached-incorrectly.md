---
title: "ACSD-48784 : prix des segments clients incorrectement mis en cache entre les groupes de clients"
description: Appliquez le correctif ACSD-48784 pour résoudre le problème Adobe Commerce en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784 : les prix des segments clients sont incorrectement mis en cache entre les groupes de clients.

Le correctif ACSD-48784 corrige le problème en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 est installé. L’ID de correctif est ACSD-48784. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les prix des segments clients sont incorrectement mis en cache entre les groupes de clients.

<u>Conditions préalables</u> :

Configurez [!DNL Varnish] ou [!DNL Fastly].

<u>Étapes à reproduire</u> :

1. Activez la mise en cache complète des pages dans votre boutique.
1. Connectez-vous au site en tant qu’utilisateur disposant de tarifs spéciaux pour les groupes de clients.
1. Accédez à la page produit d’un produit avec des tarifs spéciaux pour le groupe de clients. Observez le *prix spécial*.
1. Dans un navigateur distinct, ouvrez la même page de produit qu’un utilisateur invité sans vous connecter. Observez le prix régulier.
1. Accédez à l’interface d’administration Adobe Commerce et effacez le cache Adobe Commerce et [!DNL Fastly] de ce magasin.
1. Dans le navigateur connecté, supprimez le cookie `X-Magento-Vary`.
1. Dans le navigateur connecté, rechargez plusieurs fois la même page de produit jusqu’à ce que la mise en cache soit complètement vidée.
1. Dans le navigateur non connecté, rechargez la page du produit pour maintenant afficher le prix du groupe de clients.

<u>Résultats attendus</u> :

La page Produit affiche le prix correct pour des groupes de clients spécifiques.

<u>Résultats réels</u> :

* Les utilisateurs invités voient le prix spécial de l’utilisateur connecté.
* Le mini panier affiche le prix correct une fois le produit ajouté.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
