---
title: '''ACSD-57045 : les réécritures d''URL provoquent une boucle de page infinie après [!UICONTROL Website Root] non coché à partir de [!UICONTROL Hierarchy]'''
description: Appliquez le correctif ACSD-57045 pour résoudre le problème Adobe Commerce où les réécritures d’URL provoquent une boucle infinie de page après que [!UICONTROL Website Root] n’a pas été coché à partir de [!UICONTROL Hierarchy].
feature: CMS
role: Admin, Developer
source-git-commit: df6cfc392f6afa4639a1ab9da52a85b8b15878d2
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---


# ACSD-57045 : les réécritures d’URL provoquent une boucle de page infinie après [!UICONTROL Website Root] non coché à partir de [!UICONTROL Hierarchy]

Le correctif ACSD-57045 corrige le problème où les réécritures d’URL provoquent une boucle infinie de page après que **[!UICONTROL Website Root]** n’a pas été coché à partir de **[!UICONTROL Hierarchy]**. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-57045. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les réécritures d’URL provoquent une boucle de page infinie après la désélection de **[!UICONTROL Website Root]** de **[!UICONTROL Hierarchy]**.

<u>Étapes à reproduire</u> :

1. Créez une page CMS nommée *Test-Parent*.
1. Créez une page nommée *Test-Child*, puis, dans la section **[!UICONTROL Hierarchy]** , sélectionnez **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** et enregistrez.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Notez qu’il existe deux nouvelles réécritures :
   * Chemin d’accès de la requête à *Test-Parent* qui pointe vers *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
   * Chemin d’accès de la requête à *Test-Child* qui pointe vers *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
1. Visitez le storefront et ajoutez *test-child* à l’URL. Vous devriez voir la page enfant.
1. Faites la même chose, mais ajoutez *test-parent/test-child/* à l’URL et affichez la même page.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** et sélectionnez **[!UICONTROL Add URL Rewrite]**. Choisissez les paramètres suivants :
   * Type : *Personnalisé*
   * Chemin d’accès de la requête : *test-parent/test-child*
   * Chemin d’accès cible : *test-child*
   * Type de redirection : *Permanent (301)*
1. Visitez le chemin *test-parent/test-child* et vous devriez être redirigé vers *test-child*.
1. Modifiez la page Enfant (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Sélectionner un enfant et sélectionnez **[!UICONTROL Edit]**).
1. Dans la section **[!UICONTROL Hierarchy]**, conservez *Test-Parent* sélectionné mais désélectionnez **[!UICONTROL Website Root]** et enregistrez.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** et notez que la redirection d&#39;origine *test-child* vers *cms/page/view/page_id* est manquante. À ce stade, elle est remplacée par un chemin qui pointe *test-child* vers *test-parent/test-child*.
1. Visitez le storefront et essayez de visiter la page *Test-Child* .

<u>Résultats attendus</u> :

La page *Test-Child* est ouverte.

<u>Résultats réels</u> :

La page *Test-Child* n’est pas ouverte. Le navigateur tente d’ouvrir la page *test-parent/test-child* en boucle infinie.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
