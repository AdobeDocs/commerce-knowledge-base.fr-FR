---
title: '''ACSD-56515 : l''administrateur avec des autorisations au niveau du site web ne peut pas modifier [!UICONTROL Dynamic Block]'''
description: Appliquez le correctif ACSD-56515 pour résoudre le problème Adobe Commerce en raison duquel l’administrateur avec des autorisations au niveau du site web ne peut pas ajouter ni modifier le [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515 : L&#39;administrateur disposant d&#39;autorisations au niveau du site web ne peut pas modifier [!UICONTROL Dynamic Block]

Le correctif ACSD-56515 corrige le problème en raison duquel l’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier le [!UICONTROL Dynamic Block]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 est installé. L’ID de correctif est ACSD-56515. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier le [!UICONTROL Dynamic Block].

<u>Étapes à reproduire</u> :

1. Créez un site web secondaire avec magasin et storeview.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** et créez un rôle d’utilisateur limité à la portée du site web secondaire avec toutes les ressources disponibles.
1. Créez un utilisateur administrateur avec le rôle créé ci-dessus.
1. Connectez-vous avec l’utilisateur administrateur restreint et créez un [!UICONTROL Dynamic Block].

<u>Résultats attendus</u> :

L’utilisateur administrateur avec des restrictions sur le site web peut créer un [!UICONTROL Dynamic Block].

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : *D’autres autorisations sont nécessaires pour afficher cet élément*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
