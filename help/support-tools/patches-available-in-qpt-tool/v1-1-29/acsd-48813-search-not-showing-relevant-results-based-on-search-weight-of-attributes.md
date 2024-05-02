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

Le correctif ACSD-48813 corrige le problème en raison duquel la recherche n’affiche pas de résultats pertinents en fonction du poids de la recherche des attributs. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.29 est installée. L’ID de correctif est ACSD-48813. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche n’affiche pas les résultats pertinents en fonction du poids de la recherche des attributs.

<u>Étapes à reproduire</u>:

1. Installez Adobe Commerce avec des exemples de données.
1. Définissez le moteur de recherche sur [!DNL Elasticsearch].
1. Connectez-vous en tant qu’administrateur.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Ouvrez le *name* attribut.
1. Ouvrir le storefront *[!UICONTROL Properties]* .
1. Sélectionner [!UICONTROL Search Weight] = *10* à partir de la valeur de la liste déroulante.
1. Cliquez sur **[!UICONTROL Save Attribute]**.
1. Ouvrez maintenant le storefront et recherchez le mot *Précédent*.

<u>Résultats attendus</u>:

Les produits du sac à dos sont renvoyés en haut des résultats de recherche.

<u>Résultats réels</u>:

Les produits du sac à dos sont renvoyés au milieu des résultats de recherche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
