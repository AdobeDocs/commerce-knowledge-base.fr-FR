---
title: 'ACSD-56635 : les clients importés sont dupliqués lorsque le partage de compte est défini sur [!DNL Global]'
description: Appliquez le correctif ACSD-56635 pour résoudre le problème Adobe Commerce en raison duquel le client importé est dupliqué avec la même adresse électronique lorsque l’importation est utilisée avec le partage de compte défini sur [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
exl-id: abd542a1-6764-4385-97a6-b46015363b42
source-git-commit: 880fc679afc853b514fddda56e570fe1a279a3d9
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635 : Les clients importés sont dupliqués avec la même adresse électronique lors du partage du compte défini sur [!DNL Global]

Le correctif ACSD-56635 corrige le problème en raison duquel le client importé est dupliqué avec la même adresse électronique lorsque l’importation est utilisée avec le partage de compte défini sur [!DNL Global]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 est installé. L’ID de correctif est ACSD-56635. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients importés sont dupliqués avec la même adresse électronique lorsque le partage de compte est défini sur [!DNL Global].

<u>Étapes à reproduire</u> :

1. Sous Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]**, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Définissez le paramètre *[!UICONTROL Share Customer Accounts]* sur *[!DNL Global]*.
1. Créez plusieurs sites web et magasins :

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Créez un nouveau client sous le *site web principal* à partir de l’administrateur avec l’adresse électronique utilisée comme <adb@yormail.com>.
1. Sous **[!UICONTROL Admin]**, accédez à **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Sélectionnez **[!UICONTROL Customer Entity Type]** comme *[!UICONTROL Customers Main File]*.
1. Utilisez la même adresse électronique que <adb@yormail.com> sur un autre site Web, par exemple ws1. Reportez-vous à l’exemple de fichier CSV customer.csv fourni ci-dessous.
1. Effectuez l’importation pour afficher le nouvel utilisateur créé sous le site web *ws1* avec la même adresse électronique.

contenu customer.csv :

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Résultats attendus</u> :

Le client importé avec la même adresse email est mis à jour au lieu d’être dupliqué.

<u>Résultats réels</u> :

Les clients en double sont créés avec la même adresse email lors de l’utilisation de l’import client.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
