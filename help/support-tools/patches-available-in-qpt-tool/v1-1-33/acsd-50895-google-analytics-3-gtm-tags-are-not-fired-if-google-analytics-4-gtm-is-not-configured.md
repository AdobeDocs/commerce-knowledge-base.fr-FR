---
title: 'ACSD-50895: [!DNL Google Analytics] 3 Les balises GTM ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré'
description: Appliquez le correctif ACSD-50895 pour résoudre le problème Adobe Commerce où les balises GTM  [!DNL Google Analytics] 3 ne sont pas déclenchées si  [!DNL Google Analytics] 4 GTM n’est pas configuré.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895 : [!DNL Google Analytics] 3 Les balises GTM ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré

Le correctif ACSD-50895 corrige le problème en raison duquel [!DNL Google Analytics] 3 balises GTM ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 est installé. L’ID de correctif est ACSD-50895. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL Google Analytics] Les balises GTM 3 ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant qu’utilisateur administrateur.
1. Activez **[!DNL Google Analytics 3]** et **[!DNL Google Tag Manager]** dans **Admin** > **Magasin** > **Configuration** > **Ventes** > **API Google** > **Google Analytics**.
1. N’activez pas les **[!DNL Google Analytics 4]** et **[!DNL Google Tag Manager]**.
1. Ouvrez la page du produit sur Storefront.

<u>Résultats attendus</u> :

Les balises GTM sont déclenchées lorsque seule **[!DNL Google Analytics]** 3 GTM est activée.

<u>Résultats réels</u> :

Les balises GTM ne sont pas déclenchées lorsque **[!DNL Google Analytics]** 4 GTM est désactivé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
