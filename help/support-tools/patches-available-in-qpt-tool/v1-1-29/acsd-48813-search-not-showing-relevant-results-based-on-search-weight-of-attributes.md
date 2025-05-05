---
title: "ACSD-48813 : la recherche n’affiche pas les résultats pertinents en fonction du poids des attributs de recherche"
description: Appliquez le correctif ACSD-48813 pour résoudre le problème Adobe Commerce en raison duquel la recherche n’affiche pas les résultats pertinents en fonction du poids de la recherche des attributs.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813 : la recherche n’affiche pas les résultats pertinents en fonction du poids de la recherche des attributs.

Le correctif ACSD-48813 corrige le problème en raison duquel la recherche n’affiche pas de résultats pertinents en fonction du poids de la recherche des attributs. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 est installé. L’ID de correctif est ACSD-48813. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche n’affiche pas les résultats pertinents en fonction du poids de la recherche des attributs.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce avec des exemples de données.
1. Définissez le moteur de recherche sur [!DNL Elasticsearch].
1. Connectez-vous en tant qu’administrateur.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Ouvrez l’attribut *name* .
1. Ouvrez l’onglet storefront *[!UICONTROL Properties]* .
1. Sélectionnez [!UICONTROL Search Weight] = *10* dans la valeur de la liste déroulante.
1. Cliquez sur **[!UICONTROL Save Attribute]**.
1. Ouvrez maintenant le storefront et recherchez le mot *Back*.

<u>Résultats attendus</u> :

Les produits du sac à dos sont renvoyés en haut des résultats de recherche.

<u>Résultats réels</u> :

Les produits du sac à dos sont renvoyés au milieu des résultats de recherche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
