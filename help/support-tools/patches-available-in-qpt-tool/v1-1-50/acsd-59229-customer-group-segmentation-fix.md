---
title: "ACSD-59229 : mauvaise affectation des données du groupe client en raison d’une valeur X-Magento-Vary obsolète"
description: Appliquez le correctif ACSD-59229 pour résoudre le problème Adobe Commerce en raison duquel les informations relatives au groupe de clients sont enregistrées dans le mauvais segment en raison d’une valeur X-Magento-Vary obsolète dans la requête.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
source-git-commit: 41d502a85a0cbb4eb8d186e4c1e1256aec3f8740
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229 : inaffectation des données du groupe client en raison d’une valeur X-Magento-Vary obsolète

Le correctif ACSD-59229 corrige le problème en raison duquel les informations liées au groupe de clients sont enregistrées dans le mauvais segment en raison d’une valeur X-Magento-Vary obsolète dans la requête. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-59229. Veuillez noter que le problème a été corrigé dans la version 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les informations relatives aux groupes de clients sont enregistrées dans le mauvais segment en raison d’une valeur X-Magento-Vary obsolète dans la requête.

<u>Conditions préalables</u> :

Assurez-vous qu’Adobe Commerce B2B avec des exemples de données est installé et que [!DNL Varnish] est configuré.

<u>Étapes à reproduire</u> :

1. Configurez des tarifs avancés pour le [!DNL SKU 24-MB01] :
   1. [!UICONTROL Regular price] = *999$*
   1. [!UICONTROL Catalog and Tier Price] :
      * ** = *$200*
      * *Retailer* = *$30*

1. Créez deux comptes clients.
1. Affectez les deux clients au groupe **Wholesale**.
1. Ouvrez deux sessions de navigateur différentes et connectez-vous avec chaque client.
1. Accédez à la page du produit **[!UICONTROL 24-MB01]** pour chaque client et vérifiez que le prix affiché est *$200*.
1. Remplacez le groupe de clients de l’un des clients par **Retail**.
1. Effacez le cache à l’aide de la commande : `bin/magento cache:flush full_page`.
1. Actualisez la page de produits pour chaque client.

<u>Résultats attendus</u> :

1. Le client de détail peut voir le prix correct de *$30* pour le produit.
1. Le client de gros peut voir le prix correct de *$200* pour le produit.

<u>Résultats réels</u> :

1. Le client de détail peut voir le prix correct de *$30* pour le produit.
1. Le client de gros voit un prix incorrect de *$30* (prix de détail) pour le produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
