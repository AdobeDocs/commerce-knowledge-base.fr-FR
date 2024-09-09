---
title: 'ACSD-59280: `ReflectionUnionType::getName()` erreur dans les installations 2.4.4-pX'
description: Appliquez le correctif ACSD-59280 pour résoudre le problème Adobe Commerce où l’erreur "call to undefined method ReflectionUnionType::getName()" survient lors de l’installation des versions 2.4.4-pX.
feature: Install, Upgrade
role: Admin, Developer
source-git-commit: a7a42520c6c7d74e995d104271afa2b15b537de7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-59280 : `ReflectionUnionType::getName()` erreur dans les installations 2.4.4-pX

Le correctif ACSD-59280 corrige le problème d’erreur `call to undefined method ReflectionUnionType::getName()` lors de l’installation des versions 2.4.4-pX. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-59280. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`ReflectionUnionType::getName()` erreur lors de l’installation 2.4.4-pX.

<u>Étapes à reproduire</u> :

Effectuez une nouvelle installation à l’aide de *[!UICONTROL Composer]*.

<u>Résultats attendus</u> :

Le processus d’installation se termine sans erreur.

<u>Résultats réels</u> :

L’erreur suivante s’affiche pendant le processus `setup:upgrade` :

`Call to undefined method ReflectionUnionType::getName()`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
