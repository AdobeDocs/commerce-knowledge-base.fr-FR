---
title: '''ACSD-46683 : les prix d''expédition affichent *Pas encore calculé*'''
description: Appliquez le correctif ACSD-46683 pour résoudre le problème Adobe Commerce où le prix d’expédition affiche *Pas encore calculé*.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683 : Le prix de livraison affiche *Non encore calculé*

Le correctif ACSD-46683 corrige le problème où le prix d’expédition affiche *Non encore calculé*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 est installé. L’ID de correctif est ACSD-46683. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix d’expédition affiche *Non encore calculé*.

<u>Conditions préalables</u> :

Les modules Adobe Commerce Inventory management (MSI) sont installés.

<u>Étapes à reproduire</u> :

1. Créez un produit simple et définissez son prix sur *$34*.
1. Configurez le mode de livraison de la livraison gratuite.
1. Configurez au moins une méthode de diffusion supplémentaire.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** et créez une nouvelle règle :
   * Nom = *75more*
   * Bon = Aucun
   * Priorité = 1
   * Conditions : le sous-total est égal ou supérieur à *$75*
   * Actions :
      * Appliquer au montant de la livraison = Oui
      * Ignorer les règles suivantes = Non
      * Expédition gratuite = Pour les envois avec les articles correspondants
1. Créez une autre règle de prix de panier :
   * Nom = *35off*
   * Priorité = 0
   * Bon = coupon spécifique
   * Code coupon = 35 off
   * Actions :
      * Appliquer = Pourcentage de remise sur le prix du produit
      * Montant de la remise = 35
      * Appliquer au montant de l’expédition = Non
      * Ignorer les règles suivantes = Oui
      * Livraison gratuite = Non
1. Ouvrez le storefront et ajoutez trois produits au panier afin que le sous-total dépasse 75 $.
1. Passez à la caisse en tant qu’invité.
1. À l’étape d’expédition, sélectionnez **$0 - expédition gratuite** et passez à l’étape de paiement.
1. Vérifiez le [!UICONTROL Order Summary] à l’étape de paiement. Il affiche *[!UICONTROL $0 - Free Shipping - Free]*.
1. Appliquez le code de coupon *35off*. Le sous-total sera mis à jour et sera inférieur à 75 $.
1. Vérifiez [!UICONTROL Order Summary] à l’étape de paiement.

<u>Résultats attendus</u> :

Le message suivant s&#39;affiche : *La méthode d&#39;expédition sélectionnée n&#39;est pas disponible. Sélectionnez une autre méthode de livraison pour cette commande.*

<u>Résultats réels</u> :

Le prix de livraison affiche *Non encore calculé*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
