---
title: 'ACSD-55414 : Mauvaise performance lorsque MariaDB tente de mouler les entitys_ids'
description: Appliquez le correctif ACSD-55414 pour résoudre le problème Adobe Commerce lorsque la MariaDB tente de convertir &grave;entitys_ids&grave; de chaîne en entier, ce qui entrave les performances de la réindexation.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414 : Mauvaise performance lorsque MariaDB tente de mouler le `entitys_ids`

Le correctif ACSD-55414 corrige le problème qui entravait les performances de la réindexation lorsque la MariaDB tentait de convertir `entitys_ids` de chaîne en entier. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.41 est installé. L’ID de correctif est ACSD-55414. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances de la réindexation sont amoindries lorsque la MariaDB tente de convertir le `entitys_ids` de chaîne en entier.

<u>Étapes à reproduire</u> :

1. Mettez à jour `setup/performance-toolkit/profiles/ce/small.xml` en configurant des produits simples *50000*.
1. Générez ce profil en exécutant la commande : `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Exécutez la réindexation : `bin/magento indexer:reindex catalog_product_attribute`.

<u>Résultats attendus</u> :

La réindexation prend un temps raisonnable.

<u>Résultats réels</u> :

La réindexation prend trop de temps.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
