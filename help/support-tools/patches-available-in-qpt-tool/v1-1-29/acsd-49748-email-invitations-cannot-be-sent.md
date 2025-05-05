---
title: 'ACSD-49748 : les invitations par email ne peuvent pas être envoyées'
description: Appliquez le correctif ACSD-49748 pour résoudre le problème Adobe Commerce en raison duquel les utilisateurs ne peuvent pas envoyer d’invitations par courrier électronique.
exl-id: 65de8ea9-e65c-463b-8cba-d35767d4343d
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-49748 : les invitations par email ne peuvent pas être envoyées

Le correctif ACSD-49748 corrige le problème où les utilisateurs ne peuvent pas envoyer d’invitations par courrier électronique. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 est installé. L’ID de correctif est ACSD-49748. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur *Une erreur s’est produite lors de l’envoi d’invitations* s’affiche lors de l’envoi d’invitations.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]**.
1. Créez une invitation et enregistrez-la.
1. Accédez à **[!UICONTROL Invitation Grid]** et sélectionnez toute invitation.
1. Envoyez l’invitation.

<u>Résultats attendus</u> :

Une invitation est envoyée lorsque vous cliquez sur *[!UICONTROL Send Invitation]*.

<u>Résultats réels</u> :

L’erreur *Une erreur s’est produite lors de l’envoi des invitations* s’affiche et l’invitation n’est pas envoyée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.
