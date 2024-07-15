---
title: "ACSD-50815 : La quantité décimale pour un produit simple ne peut pas être utilisée pour la nouvelle option de produit groupé"
description: Appliquez le correctif ACSD-50815 pour résoudre le problème Adobe Commerce en raison duquel la quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815 : La quantité décimale pour un produit simple ne peut pas être utilisée pour la nouvelle option de produit groupé.

Le correctif ACSD-50815 corrige le problème en raison duquel la quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 est installé. L’ID de correctif est ACSD-50815. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant qu’administrateur.
1. Créez un produit simple.
   * Dans la fenêtre **[!UICONTROL Advanced Inventory]**, définissez [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Enregistrez le produit simple.
1. Créez un produit fourni.
1. Ajoutez n’importe quelle option.
1. Ajoutez le produit simple dans cette option.
1. Définissez une quantité décimale pour le produit simple dans l’option de produit regroupé. Par exemple, 1.5.

<u>Résultats attendus</u> :

Il est possible de définir une quantité décimale. Aucune erreur ne s’affiche.

<u>Résultats réels</u> :

L&#39;erreur, *Entrez un nombre valide dans ce champ* s&#39;affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
