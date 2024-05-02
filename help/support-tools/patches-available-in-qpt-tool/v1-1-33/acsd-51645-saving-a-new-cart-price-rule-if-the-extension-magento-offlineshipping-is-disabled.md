---
title: "ACSD-51645 : enregistrement d’une nouvelle règle de prix du panier si l’extension Magento_OfflineShipping est désactivée"
description: Appliquez le correctif ACSD-51645 pour corriger le problème Adobe Commerce qui se produit lorsqu’une erreur se produit lors de l’enregistrement d’une nouvelle règle de prix du panier si l’extension Magento_OfflineShipping est désactivée.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645 : Enregistrement d’une nouvelle règle de prix du panier si l’extension Magento_OfflineShipping est désactivée

Le correctif ACSD-51645 corrige le problème d’erreur lors de l’enregistrement d’une nouvelle règle de prix du panier si l’extension Magento_OfflineShipping est désactivée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.33 est installée. L’ID de correctif est ACSD-51645. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Obtention d’une erreur lors de l’enregistrement d’une nouvelle règle de prix du panier si l’extension `Magento_OfflineShipping` est désactivée.

<u>Étapes à reproduire</u>:

1. Désactivez la fonction `Magento_OfflineShipping` module .
1. Connexion à **Administration**.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Créer **[!UICONTROL Cart Price Rule]**.
1. Renseignez les champs obligatoires.
1. Enregistrez le **[!UICONTROL Cart Price Rule]**.

<u>Résultats attendus</u>:

La règle Prix du panier a été enregistrée avec succès.

<u>Résultats réels</u>:

L’erreur suivante se produit :
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
