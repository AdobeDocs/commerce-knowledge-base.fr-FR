---
title: "ACSD-53347 : les performances d’indexation des prix dégrade progressivement les heures supplémentaires"
description: Appliquez le correctif ACSD-53347 pour résoudre le problème Adobe Commerce où les performances se dégradent progressivement lors de la réindexation des prix pour un catalogue de produits volumineux.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347 : les performances d’indexation des prix dégrade progressivement les heures supplémentaires

Le correctif ACSD-53347 corrige le problème où les performances se dégradent progressivement lors de la réindexation des prix pour un catalogue de produits volumineux. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 est installé. L’ID de correctif est ACSD-53347. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la réindexation des prix pour un catalogue de produits volumineux, les performances des requêtes exécutées lors du processus d’indexation se dégradent progressivement.

<u>Étapes à reproduire</u> :

1. Créez un catalogue simple volumineux et affectez des options personnalisées à ces produits (les options personnalisées utilisent une table temporaire lors de l’indexation).
1. Créez au moins 200 groupes de clients ou plus pour accroître la visibilité du problème.
1. Créez au moins dix sites web et affectez tous les produits à chacun d’eux.
1. Notez que les produits importés sont presque identiques, ne diffèrent que par SKU et nom.
1. Activez **[!UICONTROL DB Logging]**.
1. Exécutez la commande `bin/magento index:reindex catalog_product_price`.
1. Recherchez *DELETE FROM`catalog_product_index_price_opt_agr_temp`* dans le `db.log`.

<u>Résultats attendus</u> :

L’exécution des *requêtes DB* s’exécute efficacement.

<u>Résultats réels</u> :

Les performances des *requêtes DB* sur les tables temporaires deviennent lentes au fil du temps, de sorte que la table d’indexation de prix prend beaucoup de temps à se terminer.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
