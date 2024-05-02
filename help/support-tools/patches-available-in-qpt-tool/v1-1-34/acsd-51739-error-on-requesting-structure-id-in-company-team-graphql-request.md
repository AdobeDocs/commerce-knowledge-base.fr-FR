---
title: '"ACSD-51739 : Erreur lors de la demande `structure_id` dans la demande GraphQL "CompanyTeam`"'
description: Appliquez le correctif ACSD-51739 pour résoudre le problème Adobe Commerce en raison duquel une erreur est renvoyée lorsque le `structure_id` est demandé dans une requête GraphQL "CompanyTeam`.
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739 : Erreur lors de la demande `structure_id` in `CompanyTeam` Requête GraphQL

Le correctif ACSD-51739 corrige le problème en raison duquel une erreur est renvoyée lorsque la variable `structure_id` est demandé dans une `CompanyTeam` Requête GraphQL. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.34 est installée. L’ID de correctif est ACSD-51739. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur est renvoyée lorsque la variable `structure_id` est demandé dans une `CompanyTeam` Requête GraphQL.

<u>Étapes à reproduire</u>

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**, et définissez *[!UICONTROL Enable Company]* to *Oui*.
1. Créez une société avec un utilisateur administrateur de société.
1. Créer un nouveau client (*customer1*) et affecter la société (créée ci-dessus) à ce client.
1. Sur le front-end, connectez-vous en tant qu’utilisateur administrateur de l’entreprise.
1. Créez une équipe d’entreprise et affectez-lui *customer1* à l’équipe par glisser-déposer.
1. Exécutez la requête GraphQl de la société suivante, qui inclut `CompanyTeam` avec `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Vérifiez la réponse GraphQL.

<u>Résultats attendus</u>:

Aucune erreur n’est renvoyée et toutes les données demandées sont présentes dans la réponse GraphQL.

<u>Résultats réels</u>:

* La réponse contient un *Erreur interne du serveur*.
* `var/log/exception.log` contient :

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
