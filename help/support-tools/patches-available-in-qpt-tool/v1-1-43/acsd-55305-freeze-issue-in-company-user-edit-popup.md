---
title: 'ACSD-55305 : gel des fenêtres contextuelles lors de l’édition des utilisateurs de l’entreprise dans [!UICONTROL My Account]'
description: Appliquez le correctif ACSD-55305 pour résoudre le problème Adobe Commerce où la fenêtre contextuelle [!UICONTROL Edit Company User] sur la page [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] se bloque avec un chargeur à l’écran.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305 : gel des fenêtres contextuelles lors de l’édition des utilisateurs de l’entreprise dans [!UICONTROL My Account]

Le correctif ACSD-55305 corrige le problème en raison duquel la fenêtre contextuelle [!UICONTROL Edit Company User] de la page [!UICONTROL My Account]> [!UICONTROL Company Structure] se bloque avec un chargeur sur l’écran. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 est installé. L’ID de correctif est ACSD-55305. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lorsque vous tentez d’utiliser la fenêtre contextuelle *[!UICONTROL Edit Company User]* sur la page *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]*, car elle se bloque avec un chargeur affiché à l’écran.

<u>Étapes à reproduire</u> :

1. Créez une entreprise B2B.
1. Créez un attribut à sélection multiple pour les clients.
1. Attribuez une valeur à l’attribut nouvellement créé pour l’administrateur de la société.
1. Connectez-vous en tant qu’administrateur de société.
1. Accédez au [!UICONTROL account dashboard] et accédez au **[!UICONTROL Company Structure]**.
1. Sélectionnez l’utilisateur.
1. Cliquez sur **[!UICONTROL Edit Selected]**.

<u>Résultats attendus</u> :

La fenêtre contextuelle de formulaire s’affiche avec précision, vous permettant ainsi de modifier les informations de l’entreprise.

<u>Résultats réels</u> :

La fenêtre contextuelle du formulaire s’affiche sans possibilité de modification.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
