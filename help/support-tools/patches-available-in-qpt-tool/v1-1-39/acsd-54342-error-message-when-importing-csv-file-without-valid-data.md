---
title: "ACSD-54342 : Message d’erreur lors de l’importation d’un fichier CSV sans données valides"
description: Appliquez le correctif ACSD-54342 pour résoudre le problème Adobe Commerce en raison duquel un message d’erreur incorrect se produit lors de l’importation d’un fichier CSV sans données valides.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 7f443ad8-c4b7-4294-b38f-9861e221bef2
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-54342 : Message d’erreur lors de l’importation d’un fichier CSV sans données valides

Le correctif ACSD-54342 corrige le problème d’affichage d’un message d’erreur incorrect lors de l’importation d’un fichier CSV sans données valides. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.39 est installé. L’ID de correctif est ACSD-54342. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message d’erreur incorrect se produit lors de l’importation d’un fichier CSV sans données valides.

<u>Étapes à reproduire</u> :

1. Créez un fichier d&#39;import contenant uniquement des données non valides (Exemples : [!DNL SKUs] qui n&#39;existent pas, champs d&#39;adresse client non valides ou adresses email client incorrectes).
1. Importez le fichier, en sélectionnant pour ignorer les erreurs de validation.

<u>Résultats attendus</u> :

La validation échoue avec le message `There are no valid rows to import`.

<u>Résultats réels</u> :

La validation réussit, mais l’importation échoue avec le message `Error in data structure: values are mixed`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
