---
title: "ACSD-51636 : l’administrateur de la société ne peut pas ajouter de nouveaux utilisateurs à partir de la section du compte client"
description: Appliquez le correctif ACSD-51636 pour résoudre le problème Adobe Commerce en raison duquel l’administrateur de la société ne peut pas ajouter de nouveaux utilisateurs à partir de la section du compte client, même s’il dispose de tous les rôles et autorisations nécessaires.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636 : L’administrateur de la société ne peut pas ajouter de nouveaux utilisateurs à partir de la section du compte client

Le correctif ACSD-51636 corrige le problème en raison duquel l’administrateur de l’entreprise ne peut pas ajouter de nouveaux utilisateurs à partir de la section du compte client, même s’il dispose de tous les rôles et autorisations nécessaires. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 est installé. L’ID de correctif est ACSD-51636. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur de l’entreprise ne peut pas ajouter de nouveaux utilisateurs à partir de la section du compte client, même s’il dispose de tous les rôles et autorisations nécessaires.

Conditions préalables :

* Le module B2B est installé.
* La fonctionnalité d’entreprise est activée.

<u>Étapes à reproduire</u> :

1. Créez une nouvelle société.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le type **[!UICONTROL Company Admin]** sur *Customer*.
1. Connectez-vous en tant que client.
1. Accédez à **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** et ajoutez les détails de l’utilisateur et rendez-le actif.
1. Enregistrez le nouvel utilisateur.

<u>Résultats attendus</u>

L’utilisateur administrateur peut ajouter un nouvel utilisateur.

<u>Résultats réels</u>

* L’utilisateur administrateur reçoit un message d’erreur : *Quelque chose s’est mal passé*.
* L’utilisateur administrateur ne peut pas créer de client.
* Le journal contient l’erreur suivante :

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
