---
title: '''ACSD-54989 : l’administrateur de la société ne peut pas commander lorsque [!UICONTROL Enable Purchase Orders] Définissez sur Oui et [!UICONTROL Purchase Order] défini sur Non'
description: Appliquez le correctif ACSD-54989 pour résoudre le problème Adobe Commerce en raison duquel l’administrateur de la société ne peut pas passer de commandes si [!UICONTROL Enable Purchase Orders] est défini sur Oui et [!UICONTROL Purchase Order] est défini sur Non.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989 : L’administrateur de la société ne peut pas commander lorsque *[!UICONTROL Enable Purchase Orders]* défini sur *Oui* et *[!UICONTROL Purchase Order]* défini sur *Non*

Le correctif ACSD-54989 corrige le problème en raison duquel les commandes ne peuvent pas être placées si **[!UICONTROL Enable Purchase Orders]** défini sur *Oui* et **[!UICONTROL Purchase Order]** défini sur *Non*. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.40 est installée. L’ID de correctif est ACSD-54989. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs d’entreprise ne peuvent pas passer de commande lorsque **[!UICONTROL Enable Purchase Orders]** est défini sur *Oui* et **Bon de commande** défini sur *Non*.

<u>Conditions préalables</u>:

Installer [!DNL B2B] modules.

<u>Étapes à reproduire</u>:

1. Activez l’entreprise et laissez [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Non*.
1. Créez un produit simple au prix de 100.
1. Créez une société par l’intermédiaire de l’administrateur.
1. Définir [!UICONTROL **Activer les commandes d’achat**] to *Oui*.
1. Connectez-vous en tant qu’administrateur de la société sur le storefront.
1. Ajoutez le produit simple créé au panier.
1. Passez à la page de passage en caisse et cliquez sur **[!UICONTROL Place Order]** pour terminer l’achat.

<u>Résultats attendus</u>:

Vous pouvez passer une commande avec succès.

<u>Résultats réels</u>:

La variable **[!UICONTROL My Account]** s’ouvre et la commande n’est pas placée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
