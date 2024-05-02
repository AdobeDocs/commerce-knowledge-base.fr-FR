---
title: 'ACSD-46865: [!UICONTROL shipment] et [!UICONTROL credit memo] n’est pas renseigné lorsque [!UICONTROL asynchronous indexing] est activé'
description: Appliquez le correctif ACSD-46865 pour résoudre le problème Adobe Commerce où [!UICONTROL shipment] et [!UICONTROL credit memo] Les grilles ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activée.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865 : [!UICONTROL shipment] et [!UICONTROL credit memo] n’est pas renseigné lorsque [!UICONTROL asynchronous indexing] est activé

Le correctif ACSD-46865 corrige le problème où [!UICONTROL shipment] et [!UICONTROL credit memo] Les grilles ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.24 est installée. L’ID de correctif est ACSD-46865. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Shipment] et [!UICONTROL credit memo] Les grilles ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activée.

<u>Étapes à reproduire</u>:

1. Dans le [!DNL Commerce] Admin, accédez à **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *OUI*.
2. Revenez à . **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Nettoyez le cache de configuration.
4. Passer une nouvelle commande d’invité pour un produit simple.
5. Exécutez cron.
6. Ouvrez la commande dans le [!UICONTROL Commerce] Admin en accédant à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** et générer une facture et un avoir.
7. Déplacez l’ordre vers [!UICONTROL Archive].
8. Créez une autre commande pour un produit simple.
9. Exécutez cron.
10. Accédez à la nouvelle commande et générez une nouvelle expédition, une facture et un avoir.
11. Exécutez cron.
12. Vérifiez les [!UICONTROL shipments], [!UICONTROL invoices], et [!UICONTROL credit memo] grilles dans l’administrateur.

<u>Résultats attendus</u>:

Nouveau [!UICONTROL shipment], [!UICONTROL invoice] et [!UICONTROL credit memo] s’affichent.

<u>Résultats réels</u>:

Nouveau [!UICONTROL shipment], [!UICONTROL invoice], et [!UICONTROL credit memo] ne s’affichent pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
