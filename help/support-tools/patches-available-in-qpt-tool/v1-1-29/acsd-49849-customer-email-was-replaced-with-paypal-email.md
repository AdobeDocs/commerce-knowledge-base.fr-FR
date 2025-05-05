---
title: '''ACSD-49849 : l''email du client a été remplacé par l''email PayPal'''
description: Appliquez le correctif ACSD-49849 pour résoudre le problème Adobe Commerce en raison duquel l’email du client a été remplacé par l’email PayPal lors du passage d’une commande avec PayPal Express via GraphQL.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849 : l&#39;email du client est remplacé par l&#39;email [!DNL PayPal]

Le correctif ACSD-49849 corrige le problème en raison duquel l’email d’un client est remplacé par un email [!DNL PayPal's] lors du placement d’une commande avec [!DNL PayPal Express] via GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 est installé. L’ID de correctif est ACSD-49849. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’email d’un client est remplacé par un [!DNL PayPal's] email lors du placement d’une commande avec [!DNL PayPal Express] via GraphQL.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Activez et configurez [!DNL PayPal Express] et définissez **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un produit simple.
1. Effectuez le paiement des invités à l’aide de GraphQL. Pour plus d’informations, reportez-vous au [tutoriel de passage en caisse GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) dans la documentation Adobe Commerce Developer.
1. Utilisez [!DNL PayPal Express] comme méthode de paiement.
1. Notez l’e-mail que vous avez utilisé à l’étape où vous [configurez votre e-mail pour le panier](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) dans la documentation du développeur Adobe Commerce.
1. Une fois la commande passée, accédez à l’administrateur Adobe Commerce et vérifiez l’email dans l’ordre créé.

<u>Résultats attendus</u> :

L’email est le même que celui défini lors de l’extraction.

<u>Résultats réels</u> :

L’e-mail défini lors du passage en caisse est remplacé par l’e-mail défini dans le compte [!DNL PayPal].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
