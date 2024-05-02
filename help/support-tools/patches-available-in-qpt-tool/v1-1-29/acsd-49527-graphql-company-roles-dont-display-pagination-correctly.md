---
title: "ACSD-49527 : les rôles de société GraphQL n’affichent pas correctement la pagination"
description: Appliquez le correctif ACSD-49527 pour résoudre le problème Adobe Commerce en raison duquel les rôles de l’entreprise GraphQL n’affichent pas correctement la pagination.
exl-id: e2d50081-8002-490e-9476-a19ba6623bda
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49527 : les rôles de société GraphQL n’affichent pas correctement la pagination

Le correctif ACSD-49527 corrige le problème en raison duquel les rôles de l’entreprise GraphQL n’affichent pas correctement la pagination. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.29 est installée. L’ID de correctif est ACSD-49527. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les rôles d’entreprise GraphQL n’affichent pas correctement la pagination.

<u>Étapes à reproduire</u>:

1. Activez la société B2B.
1. Sur le storefront, créez une nouvelle société.
1. Créez au moins deux nouveaux rôles pour cette entreprise. Il existe donc un total de trois rôles, car un rôle est le rôle par défaut.
1. Envoi d’une requête GraphQL pour obtenir des rôles spécifiant [!UICONTROL pageSize]: 2.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. Vérifiez la réponse GraphQL.

<u>Résultats attendus</u>:

`total_count: 3` et `total_pages: 2` sont renvoyés dans la réponse GraphQL.

<u>Résultats réels</u>:

`total_count: 2` et `total_pages: 1` sont renvoyés dans la réponse GraphQL.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
