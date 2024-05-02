---
title: "ACSD-56858 : incohérence des autorisations de rôle dans l’administration de la société B2B"
description: Appliquez le correctif ACSD-56858 pour résoudre le problème Adobe Commerce en raison duquel les autorisations de rôle s’affichent incorrectement pour un administrateur de société restreint dans l’environnement B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858 : incohérence des autorisations de rôle dans l’administration de la société B2B

Le correctif ACSD-56858 corrige le problème en raison duquel les autorisations de rôle s’affichent incorrectement pour un administrateur de société restreint dans l’environnement B2B. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.47 est installée. L’ID de correctif est ACSD-56858. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les autorisations de rôle pour un administrateur de société restreint dans l’environnement B2B s’affichent incorrectement.

<u>Étapes à reproduire</u>:

1. Commencez par configurer une société, en ajoutant un administrateur de société et des utilisateurs de société.
1. Connectez-vous en tant qu’administrateur de l’entreprise au storefront et créez différents rôles pour différents utilisateurs.
1. Attribuez ces rôles si nécessaire, par exemple en limitant l’accès à certaines tâches tout en autorisant un accès complet à d’autres.
1. Attribuez ces rôles à un utilisateur autre que l’administrateur de l’entreprise avec un accès complet.
1. Connectez-vous à un utilisateur administrateur autre que votre société, par exemple un gestionnaire_société.
1. Accédez à **[!UICONTROL Roles and permission]** et modifiez le rôle.
1. Notez que les autorisations affichées ne correspondent pas aux autorisations définies dans la base de données de l’entreprise pour cet ID de rôle.

<u>Résultats attendus</u>:

Les rôles et les autorisations s’affichent correctement pour l’utilisateur administrateur autre que l’entreprise.

<u>Résultats réels</u>:

Les rôles ne s’affichent pas correctement pour l’utilisateur administrateur non-société, conformément aux enregistrements de base de données dans le tableau des autorisations.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
