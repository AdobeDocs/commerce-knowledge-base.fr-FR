---
title: '''ACSD-51890: [!UICONTROL Submit review] peut être cliqué plusieurs fois"'
description: Appliquez le correctif ACSD-51890 pour résoudre le problème Adobe Commerce où la variable [!UICONTROL Submit Review] peut être cliqué plusieurs fois sans [!DNL Google reCAPTCHA v3] validation.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890 : **[!UICONTROL Submit Review]** peut être cliqué plusieurs fois sans **[!DNL Google reCAPTCHA v3]** validation

>[!NOTE]
>
>Ce correctif est remplacé par [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

Le correctif ACSD-51890 corrige le problème en raison duquel la variable **[!UICONTROL Submit Review]** peut être cliqué plusieurs fois sans **[!DNL Google reCAPTCHA v3]** validation. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.35 est installée. L’ID de correctif est ACSD-51890. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La variable **[!UICONTROL Submit Review]** peut faire l’objet de plusieurs clics sans le bouton **[!DNL Google reCAPTCHA v3]** validation.

<u>Étapes à reproduire</u>:

1. Activer **[!DNL Google reCAPTCHA v3]** pour la révision du produit.
1. Ouvrez la page produit et accédez à la **[!UICONTROL Review]** et assurez-vous que la variable [!DNL reCAPTCHA] est visible.
1. Remplissez le formulaire de révision et cliquez sur le bouton **[!UICONTROL Submit Review]** plusieurs fois plus rapidement que possible.
1. Ouvrez le **[!UICONTROL Review]** de la section Admin.

<u>Résultats attendus</u>

Les révisions en double ne sont pas créées.

<u>Résultats réels</u>

Des révisions en double sont créées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
