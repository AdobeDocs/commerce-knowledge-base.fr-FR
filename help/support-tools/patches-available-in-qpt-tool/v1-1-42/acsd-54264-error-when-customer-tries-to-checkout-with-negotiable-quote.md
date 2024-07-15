---
title: 'ACSD-54264 : erreur lorsque le client tente d’extraire avec un guillemet négociable'
description: 'Appliquez le correctif ACSD-54264 pour résoudre le problème Adobe Commerce en raison duquel un message d’erreur "Vous ne pouvez pas mettre à jour l’attribut demandé. Identifiant de ligne : store_id" apparaît lorsqu’un client tente d’extraire avec un guillemet négociable provenant d’une autre vue de magasin.'
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264 : une erreur s’affiche lorsque le client tente d’extraire avec un devis négociable

Le correctif ACSD-54264 corrige le problème lorsqu’un message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. Identifiant de ligne : store_id* s’affiche lorsqu’un client tente d’extraire avec un guillemet négociable provenant d’une autre vue de magasin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 est installé. L’ID de correctif est ACSD-54264. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. Identifiant de ligne : store_id* s’affiche lorsqu’un client tente d’extraire avec un guillemet négociable provenant d’une autre vue de magasin.

<u>Conditions préalables</u> :

Les modules Adobe Commerce B2B sont installés et activés.

<u>Étapes à reproduire</u> :

1. Créez une vue de magasin supplémentaire pour le site web par défaut.
1. Activez le *[!UICONTROL B2B Quote]* dans la configuration.
1. Connectez-vous en tant que client d’entreprise dans l’une des vues de magasin.
1. Ajoutez un produit au *[!UICONTROL Shopping Cart]*.
1. Envoyez le devis pour révision.
1. En tant qu’utilisateur administrateur, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** et envoyez le devis approuvé.
1. En tant que client de l’entreprise, définissez la vue du magasin sur une autre vue du magasin.
1. Essaie de régler.

<u>Résultats attendus</u> :

Le client passe une commande avec ce devis.

<u>Résultats réels</u> :

* L’erreur se produit lors de l’enregistrement des informations d’expédition :

  `You cannot update the request attribute. Row ID: store_id =#`

* L’erreur suivante est consignée :

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
