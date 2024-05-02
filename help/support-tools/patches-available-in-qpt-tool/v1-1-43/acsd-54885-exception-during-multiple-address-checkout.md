---
title: "ACSD-54885 : exception lors du passage en caisse de plusieurs adresses lorsque l’administrateur se connecte en tant que client"
description: Appliquez le correctif ACSD-54885 pour résoudre le problème Adobe Commerce où une erreur se produit lors du passage en caisse de plusieurs adresses lorsque l’administrateur utilise le *[!UICONTROL Login as Customer]* .
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885 : exception lors du passage en caisse de plusieurs adresses lorsque l’administrateur se connecte en tant que client

Le correctif ACSD-54885 corrige le problème lorsqu’une erreur se produit lors du passage en caisse de plusieurs adresses lorsque l’administrateur utilise la variable *[!UICONTROL Login as Customer]* . Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.43 est installée. L’ID de correctif est ACSD-54885. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lors de l’extraction de plusieurs adresses lorsque l’administrateur utilise la variable *[!UICONTROL Login as Customer]* .

<u>Étapes à reproduire</u>:

1. Assurez-vous que *[!UICONTROL Login as Customer]* est activée. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Créez un produit simple.
1. Créez un compte client avec une adresse.
1. Accédez au compte client en arrière-plan :

   * Accédez au **[!UICONTROL Account Information]** et définissez *[!UICONTROL Allow remote shopping assistance]* = *Oui*.
   * Cliquez sur **[!UICONTROL Login as Customer]**.

1. Ajoutez le produit au panier et passez à *[!UICONTROL Checkout with multiple addresses]*.
1. Mettez à jour la quantité du produit.
1. Essayez de retourner au panier.

<u>Résultats attendus</u>:

Vous pouvez mettre à jour le panier et utiliser le paiement à plusieurs adresses.

<u>Résultats réels</u>:

L’erreur suivante s’affiche lorsque vous revenez au panier.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
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
