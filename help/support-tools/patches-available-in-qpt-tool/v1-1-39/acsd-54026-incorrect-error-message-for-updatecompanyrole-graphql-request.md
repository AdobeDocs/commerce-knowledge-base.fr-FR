---
title: "ACSD-54026 : message d’erreur incorrect pour la demande GraphQL updateCompanyRole"
description: Appliquez le correctif ACSD-54026 pour résoudre le problème Adobe Commerce en raison duquel un message d’erreur incorrect s’affiche pour une requête updateCompanyRole GraphQL pour un utilisateur non autorisé.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026 : message d’erreur incorrect pour la requête GraphQL `updateCompanyRole`

Le correctif ACSD-54026 corrige le problème en raison duquel un message d’erreur incorrect s’affiche pour une requête GraphQL `updateCompanyRole` pour un utilisateur non autorisé. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.39 est installé. L’ID de correctif est ACSD-54026. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Obtention d’un message d’erreur incorrect pour une requête GraphQL `updateCompanyRole` pour un utilisateur non autorisé.

<u>Étapes à reproduire</u> :

1. Activez la société B2B dans la configuration.
1. Créez une société.
1. Envoyez une requête GraphQL `updateCompanyRole` sans transmettre de jeton porteur ou avec un jeton porteur non valide.
1. Observez le message d’erreur dans la réponse GraphQL.

<u>Résultats attendus</u> :

Vous recevez le message d&#39;erreur suivant : *Le client actuel n&#39;est pas autorisé.*

<u>Résultats réels</u> :

Vous recevez le message d’erreur suivant : *Le client n’est pas un utilisateur de l’entreprise.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
