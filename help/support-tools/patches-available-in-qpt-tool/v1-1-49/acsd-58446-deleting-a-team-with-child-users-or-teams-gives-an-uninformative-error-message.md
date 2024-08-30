---
title: 'ACSD-58446 : la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL donne un message d’erreur informatif '
description: Appliquez le correctif ACSD-58446 pour résoudre le problème Adobe Commerce en raison duquel la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur non informatif incompatible avec l’interface utilisateur.
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446 : La suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL génère un message d’erreur informatif.

Le correctif ACSD-58446 corrige le problème Adobe Commerce où la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur non informatif incompatible avec l’interface utilisateur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-58446. Veuillez noter que le problème doit être corrigé dans Adobe Commerce B2B 1.5.1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec Adobe Commerce et les versions de Magento Open Source :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur non informatif incompatible avec l’interface utilisateur.

## Conditions préalables :

Installation des modules B2B.

<u>Étapes à reproduire</u> :

1. Activez la fonctionnalité *[!UICONTROL Company]* .
1. Créez un compte d’entreprise.
1. Connectez-vous à **[!UICONTROL Admin]** et rendez le compte de la société actif.
1. Vérifiez l’adresse électronique et définissez un mot de passe pour le nouveau compte de société.
1. Créez une nouvelle équipe pour l’entreprise.
1. Connectez-vous en tant que **[!UICONTROL company user]** sur le front-end et ajoutez un **[!UICONTROL new user]** pour l’équipe créée.
1. Connectez-vous à **[!UICONTROL Admin]**, désactivez l’utilisateur de la société et définissez *[!UICONTROL Customer Active]* = *Non*
1. Veillez à supprimer l’équipe créée via GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Résultats attendus</u> :

Un message d’erreur informatif cohérent avec l’interface utilisateur est renvoyé.

<u>Résultats réels</u> :

Un message d’erreur de serveur interne générique est renvoyé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
