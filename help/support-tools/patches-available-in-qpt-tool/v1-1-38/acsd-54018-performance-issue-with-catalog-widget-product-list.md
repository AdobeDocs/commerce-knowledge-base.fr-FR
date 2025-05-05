---
title: "ACSD-54018 : problème de performance avec la liste de produits des widgets de catalogue"
description: Appliquez le correctif ACSD-54018 pour résoudre le problème Adobe Commerce en raison duquel la page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018 : problème de performance avec la liste de produits du widget de catalogue

Le correctif ACSD-54018 corrige le problème en raison duquel la page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec condition et type d’attribut booléen. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 est installé. L’ID de correctif est ACSD-54018. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen.

<u>Étapes à reproduire</u> :

1. Générer 100 000 produits.
1. Créez un attribut bool avec la portée définie sur [!UICONTROL Store View].
1. Attribuez un attribut à tous les jeux d’attributs.
   * Attribuez la valeur d’attribut *Yes* à tous les produits.
1. Maintenant, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et sélectionnez tous les 100 000 produits.
   * Sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Définissez l’attribut bool sur *Yes* et enregistrez-le.
   * Si vous vous êtes déconnecté à cette étape, consultez les *notes*.
1. Accédez à l’interface en ligne de commande et exécutez `php bin/magento queue:con:start product_action_attribute.update`.
   * Veillez à mettre à jour les attributs de tous les produits.
1. Accédez maintenant à **[!UICONTROL Content]** > **[!UICONTROL Pages]** et créez une page.
1. Ouvrez **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Sélectionnez *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Définissez la condition *[!UICONTROL Created attribute]* sur *[!UICONTROL Yes]* et enregistrez-la.
1. Accédez au front-end et ouvrez la page créée.
1. Désactivez le cache de la page entière et bloquez le cache HTML.
1. Vérifiez la vitesse de chargement des pages.
1. Rechargez la page quelques fois et calculez la durée moyenne de chargement.

<u>Résultats attendus</u> :

La page se charge rapidement.

<u>Résultats réels</u> :

Le chargement de la page prend entre 5 et 10 secondes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
