---
title: "ACSD-60303 : problème de placement des commandes d’administration résolu avec la minification d’HTML activée"
description: Appliquez le correctif ACSD-60303 pour résoudre le problème Adobe Commerce en raison duquel une commande de l’administrateur ne peut pas être placée si la minimisation des HTMLS est activée.
feature: Orders
role: Admin, Developer
source-git-commit: d087c7428307fa2c362986b0569db30618c5233a
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-60303 : résolution du problème d’emplacement des commandes d’administration avec la minification d’HTML activée

Le correctif ACSD-60303 corrige le problème en raison duquel une commande de l’administrateur ne peut pas être placée si la minification d’HTML est activée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-60303. Veuillez noter que le problème devrait être corrigé dans la version 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9 - 2.4.4-p10, 2.4.5-p8 - 2.4.5-p9, 2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes ne peuvent pas être placées à partir du panneau d’administration lorsque la minification d’HTML est activée.

<u>Étapes à reproduire</u> :

1. Activez la minimisation des HTMLS.
1. Définissez le **[!UICONTROL Application Mode]** sur *[!UICONTROL Production]*.
1. Créez une commande à partir du panneau Admin.

<u>Résultats attendus</u> :

La commande est passée avec succès.

<u>Résultats réels</u> :

La commande n’est pas créée et l’erreur suivante est consignée :

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
