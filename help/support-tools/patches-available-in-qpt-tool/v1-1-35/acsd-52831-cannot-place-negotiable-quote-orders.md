---
title: 'ACSD-52831 : impossible de placer des ordres de devis négociables lors de [!DNL Google reCAPTCHA v3 Invisible] enabled'
description: Appliquez le correctif ACSD-52831 pour résoudre le problème Adobe Commerce où vous ne pouvez pas placer d’ordres de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] est activée.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831 : impossible de placer des ordres de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] enabled

Le correctif ACSD-52831 corrige le problème où vous ne pouvez pas placer d’ordres de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] est activée. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-52831. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de placer des ordres de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] est activée.

<u>Étapes à reproduire</u>:

1. Activez la fonction de guillemet B2B.
1. Activer [!DNL Google reCAPTCHA v3 Invisible] sur le storefront pour permettre le passage en caisse/le placement des commandes.
1. Élevez une citation et passez à l’extraction avec cette citation.
1. Vous ne pourrez pas passer de commande en raison de l’erreur CAPTCHA.

<u>Résultats attendus</u>:

La citation passe en caisse.

<u>Résultats réels</u>:

Vous obtenez l’erreur *Échec de la validation de reCAPTCHA, veuillez réessayer.*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
