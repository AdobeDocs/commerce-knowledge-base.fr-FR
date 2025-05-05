---
title: 'ACSD-48059 : les marchands ne peuvent pas enregistrer [!UICONTROL Match product by rule] pour l’attribut Categories.'
description: Appliquez le correctif ACSD-48059 pour résoudre le problème Adobe Commerce en raison duquel les commerçants ne peuvent pas enregistrer le [!UICONTROL Match product by rule] pour l’attribut Categories .
exl-id: 97213157-1b54-4634-9c76-c9ab8fa96e17
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-48059 : Les vendeurs ne peuvent pas enregistrer le *[!UICONTROL Match product by rule]* pour l’attribut categories

Le correctif ACSD-48059 corrige le problème où les marchands ne peuvent pas enregistrer le *[!UICONTROL Match product by rule]* pour l’attribut categories dans [!DNL Visual Merchandiser]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 est installé. L’ID de correctif est ACSD-48059. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commerçants ne peuvent pas enregistrer l’attribut *[!UICONTROL Match product by rule]* pour les catégories dans [!DNL Visual Merchandiser].

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**, ajoutez des catégories.
1. Accédez à l’administrateur Adobe Commerce > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Accédez à la section [!UICONTROL Products in Category] .
   * Ajoutez une nouvelle condition *[!UICONTROL Match products by rule]* avec l’attribut categories.

<u>Résultats attendus</u> :

La catégorie est enregistrée avec succès.

<u>Résultats réels</u> :

* Vous ne pouvez pas enregistrer la catégorie avec la nouvelle règle et la nouvelle condition.
* *Un problème s’est produit lors de l’enregistrement de l’erreur category* s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
