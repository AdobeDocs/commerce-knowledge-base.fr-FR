---
title: "ACSD-49835 : [!UICONTROL Use Default Value] case à cocher non enregistrée"
description: Appliquez le correctif ACSD-49835 pour résoudre le problème Adobe Commerce en raison duquel la case à cocher [!UICONTROL Use Default Value] n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835 : [!UICONTROL Use Default Value] la case à cocher n’est pas enregistrée

Le correctif ACSD-49835 corrige le problème en raison duquel la case à cocher [!UICONTROL Use Default Value] n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 est installé. L’ID de correctif est ACSD-49835. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La case à cocher [!UICONTROL Use Default Value] n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple.

<u>Étapes à reproduire</u> :

1. Créez un **[!UICONTROL Multiple-select Attribute]** dans **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et ajoutez-le à un jeu d’attributs.
1. Accédez à un **[!UICONTROL Product]** et enregistrez **[!UICONTROL Values]** dans **[!UICONTROL All Store Views (Default Scope)]**.
1. Accédez à un **[!UICONTROL Store View Scope]** spécifique et enregistrez le produit.
1. Accédez à **[!UICONTROL Store View Scope]** et cochez la case **[!UICONTROL Use Default Value]** .

<u>Résultats attendus</u> :

Les valeurs d’attribut à sélection multiple sont correctement enregistrées lorsque la case à cocher [!UICONTROL Use Default Value] est cochée dans le [!UICONTROL Store View Scope].

<u>Résultats réels</u> :

Les valeurs d’attribut à sélection multiple ne sont pas correctement enregistrées lors de la vérification de la case à cocher [!UICONTROL Use Default Value] dans [!UICONTROL Store View Scope].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
