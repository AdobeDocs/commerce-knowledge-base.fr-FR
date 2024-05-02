---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]** bouton grisé lorsque le sous-total est supérieur au montant minimum de commande configuré'
description: Appliquez le correctif ACSD-46617 pour résoudre le problème Adobe Commerce où le **[!UICONTROL Continue to Checkout]Le bouton ** est grisé même si le sous-total est supérieur au montant minimum de commande configuré.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617 : &quot;[!UICONTROL Continue to Checkout]&quot; grisé lorsque le sous-total est supérieur à &quot;[!UICONTROL Minimum Order Amount]&quot;

Ce correctif ACSD-46617 résout le problème où la variable **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.24 est installée. L’ID de correctif est ACSD-46617. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La variable **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré.

<u>Étapes à reproduire</u>:

1. Accédez à Administration Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** et définissez les options suivantes :
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Créez un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Créez un produit au prix de 25 €.
1. Ajoutez le produit au panier.
1. Accédez au panier, sélectionnez le montant de 5 $. **[!UICONTROL Flat Rate shipping]** et appliquez le code du coupon.
1. Accédez au passage en caisse, effectuez l’expédition et accédez au **[!UICONTROL Paytment]** .
1. Retournez dans le panier.

<u>Résultats attendus</u>:

Aucune erreur n’est liée au montant minimum de la commande, car le total général de 2,4 $ est supérieur au montant requis de 2 $.

<u>Résultats réels</u>:

* Une erreur s’est produite lors de la création du montant minimum de commande, même si le total général de 2,4 $ est supérieur au montant minimum de commande de 2 $.
* La variable **[!UICONTROL Continue to Checkout]** est grisé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
