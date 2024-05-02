---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* statut non appliqué pour *[!UICONTROL Related Product Rules]*'
description: Appliquez le correctif ACSD-54739 pour résoudre le problème Adobe Commerce où *[!UICONTROL Product Stock]* status n’est pas appliqué pour *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739 : *[!UICONTROL Product stock]* statut non appliqué pour *[!UICONTROL Related Product Rules]*

Le correctif ACSD-54739 corrige le problème en raison duquel la variable *[!UICONTROL Product stock]* n’est pas appliquée pour *[!UICONTROL Related Product Rules]*. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.43 est installée. L’ID de correctif est ACSD-54739. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*[!UICONTROL Product stock]* n’est pas appliquée pour *[!UICONTROL Related Product Rules]*.

<u>Étapes à reproduire</u>:

1. Définissez la variable **[!UICONTROL Display Out of Stock Products]** configuration à *Oui*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** et défini *Oui* pour la condition de règle promo.
1. Créez la règle de produit associée. Accédez à **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Ajoutez une condition avec une quantité d’attributs (sélectionnez en stock/en rupture de stock).
1. Vérifiez les produits à l’avant-plan.

<u>Résultats attendus</u>:

Le produit en stock/en rupture de stock correspond à par *[!UICONTROL Related Product Rules]*.

<u>Résultats réels</u>:

Le produit en stock/en rupture de stock ne correspond pas à la valeur *[!UICONTROL Related Product Rules]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
