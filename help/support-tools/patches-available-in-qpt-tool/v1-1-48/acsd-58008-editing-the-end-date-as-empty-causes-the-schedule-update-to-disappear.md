---
title: "ACSD-58008 : la modification de la date de fin comme *vide* entraîne la disparition de la mise à jour du planning"
description: Appliquez le correctif ACSD-58008 pour résoudre le problème Adobe Commerce en raison duquel la modification de la date de fin comme *vide* entraîne la disparition de la mise à jour du planning.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008 : modification de la date de fin en tant que *empty* entraîne la disparition de la mise à jour du planning

Le correctif ACSD-58008 corrige le problème en raison duquel la date de fin était modifiée comme *empty* entraîne la disparition de la mise à jour du planning. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.48 est installée. L’ID de correctif est ACSD-58008. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Modifier la date de fin comme *empty* entraîne la disparition de la mise à jour du planning

<u>Étapes à reproduire</u>:

1. Connectez-vous en tant que [!UICONTROL Admin].
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** et créez une page.
1. Sélectionnez la page créée et cliquez sur **[!UICONTROL Schedule New Update]**. *(Accédez-le dans le coin supérieur droit de la page)*.
1. Créez quatre mises à jour. *(Par exemple, sous la forme d’un incrément de* 2 *minutes)*.
1. Mettez à jour le *update 2* et remplacer le temps par un temps devant le dernier *update 4*.
1. Enregistrez les mises à jour effectuées.

<u>Résultats attendus</u>:

La mise à jour du planning affiche le *update 3*.

<u>Résultats réels</u>:

La mise à jour du planning n’affiche pas le *update 3*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.