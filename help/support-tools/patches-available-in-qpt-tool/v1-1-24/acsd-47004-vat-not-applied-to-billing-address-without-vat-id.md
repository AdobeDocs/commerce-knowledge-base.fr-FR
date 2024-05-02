---
title: "ACSD-47004 : TVA non appliquée à l'adresse de facturation sans identifiant de TVA"
description: Appliquez le correctif ACSD-47004 pour résoudre le problème Adobe Commerce où la TVA n’est pas appliquée à une adresse de facturation sans identifiant de TVA.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004 : TVA non appliquée à l&#39;adresse de facturation sans identifiant de TVA

Le correctif ACSD-47004 corrige le problème où la TVA n&#39;est pas appliquée à une adresse de facturation sans ID de TVA. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)  La version 1.1.24 est installée. L’ID de correctif est ACSD-47004. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La TVA n&#39;est pas appliquée à une adresse de facturation sans identifiant de TVA.

<u>Étapes à reproduire</u>:

1. Ouvrez le [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** et définissez la variable **[!UICONTROL Enable Automatic Assignment to Customer Group]** to *[!UICONTROL Yes]*.
1. Définissez différents groupes pour les validations d’ID de TVA. Par exemple :
   ![validations de l’identifiant-TVA](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. Enregistrez un nouveau client.
1. Ajoutez une nouvelle adresse par défaut sans TVA. Par exemple :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Vérifiez que le groupe du client reste [!UICONTROL General].
1. Editez cette adresse et ajoutez un numéro de TVA valide :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Assurez-vous que le groupe du client a été remplacé par [!UICONTROL Retailer].
1. Editez l&#39;adresse et supprimez le numéro de TVA :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Résultats attendus</u>:

Le groupe de clients a été remplacé par la valeur par défaut. [!UICONTROL General] groupe automatiquement.

<u>Résultats réels</u>:

Le groupe de clients n’est pas remplacé par le groupe par défaut. [!UICONTROL General] groupe automatiquement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
