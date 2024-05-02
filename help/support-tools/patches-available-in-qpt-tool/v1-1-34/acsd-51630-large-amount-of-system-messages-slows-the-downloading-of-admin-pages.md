---
title: 'ACSD-51630 : de nombreux messages système ralentissent le téléchargement des pages d’administration'
description: Appliquez le correctif ACSD-51630 pour résoudre le problème de performances d’Adobe Commerce en raison duquel une grande quantité de messages système ralentit le téléchargement des pages d’administration.
feature: Admin Workspace, System
role: Admin
exl-id: 28f85199-625e-4299-bbca-8d2fc75df602
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-51630 : téléchargement lent de nombreux messages système des pages d’administration

Le correctif ACSD-51630 corrige le problème de performances où un grand nombre de messages système ralentissent le téléchargement des pages d’administration. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.34 est installée. L’ID de correctif est ACSD-51630. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

De nombreux messages système ralentissent le téléchargement des pages d’administration

<u>Étapes à reproduire</u>:

1. Effectuer un grand nombre de requêtes (~50 000) vers DELETE `/rest/async/v1/products/ {sku}`.
1. Accédez à **Page d’administration**.

<u>Résultats attendus</u>:

La page se charge au bon moment. Seuls les messages affichés doivent être chargés.

<u>Résultats réels</u>:

Le chargement de la page prend trop de temps. Tous les messages existants sont chargés depuis la base de données.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
