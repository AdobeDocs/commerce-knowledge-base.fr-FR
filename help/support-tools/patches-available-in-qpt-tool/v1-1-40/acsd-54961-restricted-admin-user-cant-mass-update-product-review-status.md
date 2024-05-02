---
title: "ACSD-54961 : L’utilisateur administrateur restreint ne peut pas mettre à jour en masse [!UICONTROL Product Review status]"
description: Appliquez le correctif ACSD-54961 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur restreint ne peut pas mettre à jour en masse l’état de révision du produit.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961 : L’utilisateur administrateur restreint ne peut pas mettre à jour en masse [!UICONTROL Product Review status]

Le correctif ACSD-54961 corrige le problème lorsqu’un utilisateur administrateur restreint ne peut pas mettre à jour en masse [!UICONTROL Product Review status]. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.40 est installée. L’ID de correctif est ACSD-54961. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur restreint ne peut pas mettre à jour en masse [!UICONTROL Product Review status].

<u>Étapes à reproduire</u>:

1. Créez un site web, un magasin et une vue de magasin supplémentaires.
1. Ajoutez un produit au 2e magasin, puis ajoutez une révision.
1. Créez un utilisateur administrateur restreint ayant accès uniquement au 2e magasin.
1. Connectez-vous en tant qu’utilisateur administrateur restreint, puis accédez à **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**, puis définissez la variable **État** to *Approuvé* ou *En attente*.

<u>Résultats attendus</u>:

L’utilisateur administrateur restreint peut mettre à jour les révisions à l’aide de la variable **[!UICONTROL Mass Update]** action.

<u>Résultats réels</u>:

Une erreur se produit lors de la mise à jour des révisions à l’aide de **[!UICONTROL Mass Update]** action.<br>
La variable `var/log/exception.log` contient une erreur similaire :

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
