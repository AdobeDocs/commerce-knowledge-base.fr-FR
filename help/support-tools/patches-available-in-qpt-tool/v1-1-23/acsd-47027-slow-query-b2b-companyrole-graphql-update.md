---
title: '"ACSD-47027 : requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'''
description: Appliquez le correctif ACSD-47027 pour résoudre le problème Adobe Commerce en cas de requête lente B2B. [!UICONTROL CompanyRole] [!DNL GraphQL] mettre à jour.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027 : requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update

Le correctif ACSD-47027 résout le problème où la requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] La mise à jour ne fonctionne pas comme prévu. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.23 est installée. L’ID de correctif est ACSD-47027. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Requête lente B2B [!UICONTROL CompanyRole] [!DNL GraphQL] La mise à jour ne fonctionne pas comme prévu.

<u>Conditions préalables</u>:

Installez le module B2B.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur Adobe Commerce, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** et défini **[!UICONTROL Enable Company]** to _Oui_.
1. Positionnez-vous au front-end et créez une société.
1. Une fois connecté en tant qu’utilisateur de l’entreprise, accédez à **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** et ajoutez un nouveau rôle.
1. Activer [!UICONTROL dev] journal des requêtes à l’aide de `bin/magento dev:que:enab`.
1. Maintenant, envoyez le fichier ci-dessous [!DNL GraphQL] requête (id correspond à [!UICONTROL base64] ID de rôle codé) :

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Vérifiez le journal des requêtes.
1. Vous pouvez constater que la requête ci-dessus est exécutée. Cette requête est exécutée dans `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Résultats attendus</u>:

La variable `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` doit être optimisé afin d’éviter de charger toutes les données disponibles dans la variable **[!UICONTROL company_permissions]** Table DB.

<u>Résultats réels</u>:

Adobe Commerce exécute une requête sans aucun filtre. Lorsqu’il y a un grand nombre d’enregistrements, la préparation de la collecte de données par Adobe Commerce prend beaucoup de temps.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
