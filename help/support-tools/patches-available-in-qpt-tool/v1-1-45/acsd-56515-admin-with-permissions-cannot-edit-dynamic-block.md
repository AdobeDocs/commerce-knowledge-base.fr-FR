---
title: 'ACSD-56515 : l’administrateur avec des autorisations au niveau du site web ne peut pas modifier [!UICONTROL Dynamic Block]'
description: Appliquez le correctif ACSD-56515 pour résoudre le problème Adobe Commerce en raison duquel l’administrateur avec des autorisations au niveau du site web ne peut pas ajouter ni modifier la variable [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515 : l’administrateur disposant d’autorisations au niveau du site web ne peut pas modifier [!UICONTROL Dynamic Block]

Le correctif ACSD-56515 corrige le problème en raison duquel l’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier la variable [!UICONTROL Dynamic Block]. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.45 est installée. L’ID de correctif est ACSD-56515. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier la variable [!UICONTROL Dynamic Block].

<u>Étapes à reproduire</u>:

1. Créez un site web secondaire avec magasin et storeview.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** et créer un rôle utilisateur limité à la portée du site web secondaire avec toutes les ressources disponibles.
1. Créez un utilisateur administrateur avec le rôle créé ci-dessus.
1. Connectez-vous avec l’utilisateur administrateur restreint et créez un [!UICONTROL Dynamic Block].

<u>Résultats attendus</u>:

L’utilisateur administrateur avec des restrictions sur le site web peut créer une [!UICONTROL Dynamic Block].

<u>Résultats réels</u>:

Vous obtenez l’erreur suivante : *Plus d’autorisations sont nécessaires pour afficher cet élément*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
