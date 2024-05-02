---
title: "ACSD-54680 : Citation B2B pour un produit avec plusieurs sources affectées impossible à traiter"
description: Appliquez le correctif ACSD-54680 pour résoudre le problème Adobe Commerce en raison duquel le devis B2B pour un produit avec plusieurs sources affectées ne peut pas être traité.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680 : Il n’est pas possible de traiter les guillemets B2B d’un produit avec plusieurs sources affectées.

Le correctif ACSD-54680 corrige le problème en raison duquel le devis B2B d’un produit avec plusieurs sources affectées ne peut pas être traité. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.40 est installée. L’ID de correctif est ACSD-54680. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il n’est pas possible de traiter les guillemets B2B d’un produit avec plusieurs sources affectées.

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** et créez deux nouvelles sources : **Source 1** et **Source 2**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** et créez un nouveau Stock : **Stock A**, affectez-la au site web principal, puis **Source 1** et **Source 2** à lui.
1. Créez un produit simple, attribuez **Source 1** et **Source 2**, et définissez Qté = *2* pour chaque source. (la quantité vendable du produit doit être : *4* par conséquent).
1. Créez un compte d’entreprise.
1. Accédez au **[!UICONTROL Storefront]** et connectez-vous au compte de la société.
1. Ajoutez le produit simple au panier avec qty = *4*.
1. Ouvrez le *[!UICONTROL Shopping cart]* et cliquez sur **[!UICONTROL Request a quote]** bouton .
1. Ajoutez un commentaire et un nom de guillemet, puis cliquez sur **[!UICONTROL Send a Request]** bouton .
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Ouvrez une citation récemment envoyée.

<u>Résultats attendus</u>:

Les articles cités contiennent le produit commandé.

<u>Résultats réels</u>:

La section de page éléments entre guillemets est vide et il n’est pas possible de traiter le guillemet.
`var/log/system.log` contains

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
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
