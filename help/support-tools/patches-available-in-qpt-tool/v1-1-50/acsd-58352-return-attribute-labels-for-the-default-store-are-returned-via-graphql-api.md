---
title: 'ACSD-58352 : les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via [!DNL GraphQL] API'
description: Appliquez le correctif ACSD-58352 pour résoudre le problème Adobe Commerce en raison duquel les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via l’API  [!DNL GraphQL] lorsqu’une vue de magasin autre que la vue par défaut est spécifiée dans l’en-tête de la requête.
feature: GraphQL, Returns
role: Admin, Developer
source-git-commit: 6df1ec7e2cccfbadaa88b8233ca99faf40a208c5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# ACSD-58352 : les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via l’API [!DNL GraphQL]

Le correctif ACSD-58352 corrige le problème en raison duquel les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via l’API [!DNL GraphQL] lorsqu’une vue de magasin autre que la vue par défaut est spécifiée dans l’en-tête de la requête. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-58352. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via l’API [!DNL GraphQL].

<u>Étapes à reproduire</u> :

1. Activez le **[!UICONTROL Return Merchandising Authorization]**.
1. Créez un *[!UICONTROL Additional Store]* et un *[!UICONTROL Store View]* sous le site web par défaut.
1. Modifiez l’attribut de retour **[!UICONTROL Reason for Return]** et ajoutez des libellés pour toutes les vues de magasin.
1. Créez un *[!UICONTROL Order]*.
1. Créez un *[!UICONTROL Return]* pour cette commande. Assurez-vous que l’état *[!UICONTROL Return]* est *[!UICONTROL Pending]* .
1. Envoyez une requête Customer [!DNL GraphQL] avec la valeur par défaut spécifiée [!UICONTROL Store View] dans l’en-tête :

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observez la réponse.

<u>Résultats attendus</u>

Les libellés renvoyés dans la réponse [!DNL GraphQL] correspondent au [!UICONTROL Store View] défini dans l’en-tête de la requête.

<u>Résultats réels</u> :

Les libellés renvoyés dans la réponse [!DNL GraphQL] sont pour la valeur par défaut [!UICONTROL Store View].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
