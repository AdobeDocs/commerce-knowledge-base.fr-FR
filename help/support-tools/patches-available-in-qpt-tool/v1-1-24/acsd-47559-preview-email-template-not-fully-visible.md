---
title: "ACSD-47559 : aperçu du modèle d'email pour les emails qui ne sont pas entièrement visibles"
description: Appliquez le correctif ACSD-47559 pour résoudre le problème Adobe Commerce en raison duquel l’aperçu du modèle d’email n’est pas entièrement visible.
exl-id: de8c9001-5c4f-4ef3-a80a-92d69825ecb0
feature: Communications, Marketing Tools, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-47559 : aperçu du modèle d&#39;email non complètement visible

Le correctif ACSD-47559 corrige le problème lorsque l’aperçu du modèle d’email n’est pas entièrement visible. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.24 est installé. L’ID de correctif est ACSD-47559. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;aperçu du modèle d&#39;email n&#39;est pas entièrement visible.

<u>Étapes à reproduire</u> :

* Ajoutez un modèle d&#39;email ou utilisez un modèle d&#39;email existant dans l&#39;Admin Adobe Commerce > **[!UICONTROL Marketing]** > **[!UICONTROL Communications]** > **[!UICONTROL Email Templates]**.

<u>Résultats attendus</u> :

La fenêtre de prévisualisation est mise à l&#39;échelle en fonction de la taille du modèle d&#39;email.

<u>Résultats réels</u> :

La fenêtre contextuelle d’aperçu s’ouvre avec des barres de défilement, ce qui n’est pas pratique pour prévisualiser un modèle de courrier électronique.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
