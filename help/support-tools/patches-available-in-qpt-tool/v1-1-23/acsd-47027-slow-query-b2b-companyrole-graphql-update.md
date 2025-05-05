---
title: 'ACSD-47027 : requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'
description: Appliquez le correctif ACSD-47027 pour résoudre le problème Adobe Commerce en cas de mise à jour lente de la requête B2B [!UICONTROL CompanyRole] [!DNL GraphQL] .
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027 : mise à jour de la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL]

Le correctif ACSD-47027 résout le problème où la mise à jour de la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] ne fonctionne pas comme prévu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 est installé. L’ID de correctif est ACSD-47027. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour de la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] ne fonctionne pas comme prévu.

<u>Conditions préalables</u> :

Installez le module B2B.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur Adobe Commerce, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** et définissez **[!UICONTROL Enable Company]** sur _Oui_.
1. Positionnez-vous au front-end et créez une société.
1. Une fois connecté en tant qu’utilisateur de la société, accédez à **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** et ajoutez un nouveau rôle.
1. Activez le journal de requête [!UICONTROL dev] à l’aide de `bin/magento dev:que:enab`.
1. Maintenant, envoyez la demande [!DNL GraphQL] ci-dessous (id est l&#39;ID de rôle encodé [!UICONTROL base64]) :

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Vérifiez le journal des requêtes.
1. Vous pouvez constater que la requête ci-dessus est exécutée. Cette requête est exécutée dans `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Résultats attendus</u> :

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` doit être optimisé pour éviter de charger toutes les données disponibles dans la table **[!UICONTROL company_permissions]** DB.

<u>Résultats réels</u> :

Adobe Commerce exécute une requête sans aucun filtre. Lorsqu’il y a un grand nombre d’enregistrements, la préparation de la collecte de données par Adobe Commerce prend beaucoup de temps.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
