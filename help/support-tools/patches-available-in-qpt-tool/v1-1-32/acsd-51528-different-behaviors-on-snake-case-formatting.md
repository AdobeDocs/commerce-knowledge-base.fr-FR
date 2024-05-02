---
title: 'ACSD-51528 : Différents comportements sur la mise en forme serpent_case'
description: Appliquez le correctif ACSD-51528 pour résoudre le problème Adobe Commerce où il existe différents comportements sur la mise en forme snake_case.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528 : Différents comportements sur la mise en forme snake_case

Le correctif ACSD-51528 corrige différents comportements sur la mise en forme snake_case. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.32 est installée. L’ID de correctif est ACSD-51528. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Différents comportements sur la mise en forme snake_case.

<u>Étapes à reproduire</u>:

1. Testez la variable `\Magento\Framework\Api\DataObjectHelper::populateWithArray` avec une variété de noms de propriété différents.
1. Les propriétés avec des noms tels que *NewPName* doit être transformé en *new_p_name* au lieu de cela, ils sont transformés en *new_pname*.
1. En outre, lors de l’utilisation de la variable *getNewPName* dans l’objet, *null* est renvoyée, car la variable *Modèle abstrait* transformera correctement l’appel à *new_p_name* rendant les deux fonctions incompatibles les unes avec les autres.

<u>Résultats attendus</u>

La variable **[!UICONTROL populateWithArray]** doit transformer correctement les propriétés de l’objet en snake_case, ce qui le rend compatible avec la fonction **[!DNL AbstractModel's]** `Getters` et `Setters`.

<u>Résultats réels</u>

Lors de l’utilisation de la variable **[!UICONTROL populateWithArray]** , les propriétés d’objet qui contiennent plusieurs majuscules dans une ligne de nom entraînent l’inexactitude de la transformation snake_case dans le tableau de données final.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
