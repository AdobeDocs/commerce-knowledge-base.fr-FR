---
title: "ACSD-51819 : Placement de plusieurs commandes avec un seul ID de guillemet simple"
description: Appliquez le correctif ACSD-51819 pour résoudre le problème Adobe Commerce en raison duquel plusieurs commandes peuvent être placées via le même ID de guillemet.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819 : Placement de plusieurs commandes avec un seul ID de guillemet simple

Le correctif ACSD-51819 corrige le problème en raison duquel plusieurs commandes peuvent être placées via le même ID de guillemet. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.41 est installée. L’ID de correctif est ACSD-51819. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Plusieurs commandes peuvent être placées avec le même ID de guillemet.

<u>Étapes à reproduire</u>:

1. Connectez-vous en tant qu’utilisateur.
1. Ajoutez des éléments au panier et passez à l’extraction.
1. Choisissez un mode de paiement, mais ne cliquez pas sur la variable **[!UICONTROL Place Order]** bouton .
1. Connectez-vous au même compte dans un autre navigateur.
1. Passez à l’extraction avec les mêmes éléments sans cliquer sur le bouton **[!UICONTROL Place Order]** bouton .
1. Cliquez sur le bouton **[!UICONTROL Place Order]** dans les deux systèmes en même temps.
1. Validez les commandes passées dans les deux navigateurs.

<u>Résultats attendus</u>:

Seule la première commande passée à partir d’un navigateur est traitée avec succès.

<u>Résultats réels</u>:

Les commandes ont été passées dans les deux navigateurs.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
