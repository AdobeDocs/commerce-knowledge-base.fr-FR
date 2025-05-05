---
title: "ACSD-49464 : Factures, envois et notes de crédit ne sont pas revenus de l'archive"
description: Appliquez le correctif ACSD-49464 pour résoudre le problème Adobe Commerce en raison duquel les factures, les envois et les notes de crédit ne sont pas déplacés de l’archive lorsque l’ID de commande est différent.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464 : Factures, envois et notes de crédit ne sont pas revenus de l’archive

Le correctif ACSD-49464 corrige le problème en raison duquel les factures, les envois et les notes de crédit ne sont pas renvoyés de l’archive lorsque l’ID de commande est différent. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 est installé. L’ID de correctif est ACSD-49464. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les factures, les envois et les notes de crédit ne sont pas retirés de l’archive lorsque orderId est différent.

<u>Étapes à reproduire</u> :

1. Activez l’archivage des commandes, des factures, des envois et des notes de crédit.
1. Créez et exécutez une commande, y compris l’expédition, la facture et l’avoir.
1. Assurez-vous que les identifiants d’expédition, de facture et de note de crédit ne sont pas identiques au numéro de commande.
1. Déplacez l’ordre vers lequel archiver.
1. Restaurez l&#39;ordre archivé pour gérer les commandes.
1. Vérifiez les détails des factures, des frais de livraison et des notes de crédit dans les pages de grille [!UICONTROL Invoice], [!UICONTROL Shipping] et [!UICONTROL Credit Memo] respectives.

<u>Résultats attendus</u> :

Les enregistrements associés d’origine sont restaurés lorsque la commande est déplacée de la liste d’archives vers la gestion des commandes.

<u>Résultats réels</u> :

* Aucun enregistrement pour l’expédition, la facture et les notes de crédit si tous les identifiants sont différents.
* Si la commande et les enregistrements associés ont le même identifiant, alors les enregistrements sont renvoyés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
