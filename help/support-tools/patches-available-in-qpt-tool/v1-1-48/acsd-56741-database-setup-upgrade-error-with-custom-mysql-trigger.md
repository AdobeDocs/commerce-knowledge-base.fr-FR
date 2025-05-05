---
title: "ACSD-56741 : résolution des erreurs de configuration de la base de données avec les déclencheurs MySQL personnalisés"
description: Appliquez le correctif ACSD-56741 pour résoudre le problème Adobe Commerce en raison duquel un message d’erreur *Tentative d’accès au décalage de tableau sur la valeur de type null* apparaît pendant &grave;setup:upgrade&grave; en raison d’un déclencheur MySQL personnalisé dans la base de données sans rapport avec l’indexation et [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 97839140-03c5-44f0-ba75-935d62f5bf90
source-git-commit: 7cd830d9ba4af6350a14e0cdb50439d2d07084dc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741 : résolution des erreurs de configuration de la base de données avec les déclencheurs MySQL personnalisés

Le correctif ACSD-56741 corrige le problème en raison duquel un message d’erreur *Tentative d’accès au décalage de tableau sur la valeur de type null* s’affiche pendant `setup:upgrade` en raison d’un déclencheur MySQL personnalisé dans la base de données sans rapport avec l’indexation et [!DNL MView]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 est installé. L’ID de correctif est ACSD-56741. Veuillez noter que le problème devrait être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message d’erreur *Tentative d’accès au décalage de tableau sur la valeur de type null* s’affiche pendant `setup:upgrade` en raison d’un déclencheur MySQL personnalisé dans la base de données sans rapport avec l’indexation et [!DNL MView].

<u>Étapes à reproduire</u> :

1. Exécutez `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Exécutez `php bin/magento c:f`.
1. Exécutez `php bin/magento setup:upgrade`.

<u>Résultats attendus</u> :

La mise à niveau de la configuration se termine sans erreur.

<u>Résultats réels</u> :

La mise à niveau de la configuration se termine avec un message d’erreur :

*Avertissement : tentative d’accès au décalage du tableau sur la valeur de type null*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
