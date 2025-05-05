---
title: "ACSD-53414 : les utilisateurs administrateurs à restrictions peuvent voir les pages CMS en dehors de leur portée d’autorisation"
description: Appliquez le correctif ACSD-53414 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur restreint peut voir les pages CMS en dehors de leur portée d’autorisation.
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414 : Les utilisateurs administrateurs à restrictions peuvent voir les pages CMS en dehors de leur portée d’autorisation.

Le correctif ACSD-53414 corrige le problème en raison duquel un utilisateur administrateur restreint peut voir les pages CMS en dehors de leur portée d’autorisation. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 est installé. L’ID de correctif est ACSD-53414. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs limités peuvent voir les pages CMS au-delà de leur portée d’autorisation.

<u>Étapes à reproduire</u> :

1. Créez un site web (sub_website), un magasin (sub_store) et un storeview (sub_storeview).
1. Créez un rôle de sous-expert, permettant de définir la portée de sub_website et sub_store. Attribuez uniquement les autorisations suivantes : [!UICONTROL Dashboard] et [!UICONTROL Pages].
1. Créez un utilisateur administrateur et affectez-le au rôle sub_expert.
1. Affectez les pages de CSM suivantes à sub_storeview et à l’affichage de magasin par défaut.

   * [!UICONTROL 404 Not Found] > Sous-storeview
   * [!UICONTROL 503 Service Unavailable] > Présentation par défaut

1. Connectez-vous à l’administrateur à l’aide de l’utilisateur administrateur créé à l’étape 3.
1. Vérifiez la grille de page CMS.

<u>Résultats attendus</u> :

La page *[!UICONTROL 503 Service Unavailable]* n’est pas visible par l’administrateur web.

<u>Résultats réels</u> :

*[!UICONTROL 503 Service Unavailable]* est visible par l’administrateur web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
