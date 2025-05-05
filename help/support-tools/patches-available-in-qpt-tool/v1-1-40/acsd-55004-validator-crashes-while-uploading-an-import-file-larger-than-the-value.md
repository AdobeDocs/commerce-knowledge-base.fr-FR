---
title: "ACSD-55004 : le programme de validation se bloque lors du téléchargement d’un fichier d’importation supérieur à la valeur"
description: Appliquez le correctif ACSD-55004 pour résoudre le problème Adobe Commerce en raison duquel un programme de validation se bloque lors du téléchargement d’un fichier d’importation supérieur à la valeur configurée dans &grave;php.ini&grave;.
feature: Data Import/Export
role: Admin, Developer
exl-id: 03b7667e-9b5b-4319-9135-dbc7fda7861d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-55004 : La validation se bloque lors du téléchargement d’un fichier d’importation supérieur à la valeur

Le correctif ACSD-55004 corrige le problème lorsqu’un programme de validation se bloque lors du téléchargement d’un fichier d’importation supérieur à la valeur configurée dans `php.ini`. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.40 est installé. L’ID de correctif est ACSD-55004. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le programme de validation se bloque lors du téléchargement d’un fichier d’importation supérieur à la valeur configurée dans `php.ini`.

<u>Étapes à reproduire</u> :

Essayez de télécharger un fichier d’importation plus volumineux que celui configuré dans `php.ini`.

<u>Résultats attendus</u> :

La taille du fichier est validée sans erreur.

<u>Résultats réels</u> :

La validation se bloque.

`var/log/exception.log` contient :

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
