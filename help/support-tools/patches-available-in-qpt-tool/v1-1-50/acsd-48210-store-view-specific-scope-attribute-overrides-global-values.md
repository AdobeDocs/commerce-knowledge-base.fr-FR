---
title: "ACSD-48210 : l’attribut de portée spécifique de la vue de magasin remplace les valeurs globales"
description: Appliquez le correctif ACSD-48210 pour résoudre le problème Adobe Commerce de mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique remplace les valeurs d’attribut dans la portée globale.
feature: Products, Attributes
role: Admin, Developer
source-git-commit: 0fb14710d126aa4b4d6f5b6d0c70b190dcae81ae
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48210 : les attributs de portée spécifiques de la vue de magasin remplacent les valeurs globales

Le correctif ACSD-48210 corrige le problème en raison duquel, lors de la mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique, remplace les valeurs d’attribut dans la portée globale. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-48210. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique, remplace les valeurs d’attribut dans la portée globale.

L&#39;import des prix des produits avec plusieurs lignes partageant les mêmes `SKU` et `store_view_code` a provoqué des mises à jour incorrectes des prix dans les portées *[!UICONTROL All Store View]* et *[!UICONTROL Default Store]*. La modification de l’attribut de portée du site web dans une vue de magasin spécifique ne remplace plus la valeur de l’attribut dans la portée globale.
<u>Étapes à reproduire</u> :

1. Configurez le *[!UICONTROL Catalog Price Scope]* sur *[!UICONTROL Website]*.
1. Créez un produit simple nommé *SP01* et définissez le prix sur *$84.50*.
1. Importez le produit à l’aide du fichier CSV suivant fourni ci-dessous :

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Vérifiez le prix du produit dans les portées *[!UICONTROL All Store View]* et *[!UICONTROL Default Store]*.

<u>Résultats attendus</u> :

* La première valeur non vide est utilisée pour la portée *[!UICONTROL Default Store]*.
* La portée de *[!UICONTROL All Store View]* reste inchangée.

<u>Résultats réels</u> :

* Le prix de la portée *[!UICONTROL All Store View]* change en *$86.59*.
* Le prix de la portée *[!UICONTROL Default Store]* change en *$86.59*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
