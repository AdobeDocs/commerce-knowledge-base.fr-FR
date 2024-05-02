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

# ACSD-49849 : L’email du client est remplacé par [!DNL PayPal] email

Le correctif ACSD-49849 corrige le problème en raison duquel le courrier électronique d’un client est remplacé par un [!DNL PayPal's] lors du placement d’une commande avec [!DNL PayPal Express] via GraphQL. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.29 est installée. L’ID de correctif est ACSD-49849. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’email d’un client est remplacé par un [!DNL PayPal's] lors du placement d’une commande avec [!DNL PayPal Express] via GraphQL.

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Activation et configuration [!DNL PayPal Express] et défini **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un produit simple.
1. Effectuez le paiement des invités à l’aide de GraphQL. Voir à ce sujet la section [Tutoriel sur le passage en caisse GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) dans la documentation destinée aux développeurs Adobe Commerce.
1. Utilisation [!DNL PayPal Express] comme mode de paiement.
1. Notez le courrier électronique que vous avez utilisé à l’étape où vous [configurer votre adresse électronique pour le panier ;](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) dans la documentation destinée aux développeurs Adobe Commerce.
1. Une fois la commande passée, accédez à l’administrateur Adobe Commerce et vérifiez l’email dans l’ordre créé.

<u>Résultats attendus</u>:

L’email est le même que celui défini lors de l’extraction.

<u>Résultats réels</u>:

L’e-mail défini lors du passage en caisse est remplacé par l’e-mail défini dans la variable [!DNL PayPal] compte .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
