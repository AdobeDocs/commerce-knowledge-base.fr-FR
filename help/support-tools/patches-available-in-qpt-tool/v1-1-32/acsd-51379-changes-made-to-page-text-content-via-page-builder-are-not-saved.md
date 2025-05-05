---
title: "ACSD-51379 : les modifications apportées au contenu texte de la page via [!DNL Page Builder] ne sont pas enregistrées"
description: Appliquez le correctif ACSD-51379 pour résoudre le problème Adobe Commerce en raison duquel les modifications apportées au contenu texte d’une page via  [!DNL Page Builder]  ne sont pas enregistrées.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379 : les modifications apportées au contenu texte de la page via [!DNL Page Builder] ne sont pas enregistrées

Le correctif ACSD-51379 corrige le problème en raison duquel les modifications apportées au contenu texte d’une page via [!DNL Page Builder] ne sont pas enregistrées. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 est installé. L’ID de correctif est ACSD-51379. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications apportées au contenu texte d’une page via [!DNL Page Builder] ne sont pas enregistrées.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Créez une page de test avec une ligne et un élément de texte sur l’onglet **[!UICONTROL Content]**.
1. Enregistrez la page et revenez à l’onglet **[!UICONTROL Content]** .
1. Modifiez le texte en le sélectionnant et en le modifiant.

   **Remarque :** Le problème n’est reproductible que si le texte est sélectionné et modifié sans activer l’éditeur.

1. Cliquez sur le bouton **[!UICONTROL Save and Close]** de la page de test.
1. Ouvrez à nouveau la page de test et vérifiez l’onglet **[!UICONTROL Content]** .

<u>Résultats attendus</u> :

Le nouveau texte est enregistré avec succès pour les éléments de texte d’origine et dupliqués.

<u>Résultats réels</u> :

L’élément de texte est dupliqué avec succès, mais le nouveau texte n’est pas enregistré.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
