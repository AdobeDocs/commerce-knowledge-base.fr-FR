---
title: "ACSD-48164 : l’administrateur restreint ne peut pas enregistrer la valeur au niveau du site web"
description: Appliquez le correctif ACSD-48164 pour résoudre le problème Adobe Commerce en raison duquel un administrateur restreint ne peut pas enregistrer de valeur au niveau du site web.
exl-id: 6ec15163-ad30-4566-a46c-5756bfd9f8d4
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164 : l’administrateur restreint ne peut pas enregistrer la valeur au niveau du site web

Le correctif ACSD-48164 corrige le problème lorsqu’un administrateur restreint ne peut pas enregistrer une valeur au niveau du site web. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.27 est installée. L’ID de correctif est ACSD-48164. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur restreint ne peut pas enregistrer de valeur au niveau du site web.

<u>Étapes à reproduire</u>:

1. Créez un site web, un magasin et une vue de magasin dans [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Créez un nouveau rôle d’administrateur dans [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Accédez à **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, sélectionnez le nouveau site web et affectez ce rôle à un utilisateur administrateur.

1. Sélectionnez un produit et affectez uniquement le nouveau site web. Ne sélectionnez pas le site web par défaut.
1. Connectez-vous en tant qu’utilisateur administrateur affecté à l’étape 2 et modifiez le produit sous **[!UICONTROL All Store View]** en modifiant un attribut au niveau du site web, comme *[!UICONTROL Status]*, *[!UICONTROL Tax Class]*, puis définissez le produit comme nouveau.
1. Enregistrez le produit.

<u>Résultats attendus</u>:

Un utilisateur administrateur associé à la portée du rôle à un site web peut enregistrer les attributs de produit au niveau du site web à l’aide de la variable *[!UICONTROL All Store View]* portée.

<u>Résultats réels</u>:

Le message de succès indiquant que le produit a été enregistré s’affiche, mais les valeurs de l’attribut de produit restent inchangées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
