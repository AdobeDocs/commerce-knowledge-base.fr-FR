---
title: 'MDVA-40550 : Produits manquants sur le front-end après réindexation'
description: Le correctif MDVA-40550 résout le problème en raison duquel la réindexation entraîne l’absence de certains ou de tous les produits des catégories storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 est installé. L’ID de correctif est MDVA-40550. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550 : Produits manquants sur le front-end après réindexation

Le correctif MDVA-40550 résout le problème en raison duquel la réindexation entraîne l’absence de certains ou de tous les produits des catégories storefront. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 est installé. L’ID de correctif est MDVA-40550. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Créez un produit.
1. Basculez les indexeurs vers **Mise à jour par planning**.
   * Attribuez le produit à une catégorie.
1. Activez xdebug et effectuez le point d’arrêt xdebug dans `\Magento\Indexer\Model\Indexer::reindexAll` et `\Magento\Indexer\Model\IndexMutex::execute`.
1. Exécutez une **réindexation complète** de `catalog_category_product` avec la commande :

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Attendez que l’exécution s’arrête sur le point d’arrêt `\Magento\Indexer\Model\Indexer::reindexAll`.

1. Dans une autre console, exécutez une **réindexation partielle** en parallèle avec la commande :

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Attendez que l’exécution s’arrête sur le point d’arrêt `\Magento\Indexer\Model\IndexMutex::execute`. Il verrouillera l’indexeur `catalog_category_product`.
1. Reprenez l’exécution de la réindexation complète de `catalog_category_product` et attendez un délai d’expiration du verrouillage (60 secondes).

<u>Résultats attendus</u> :

Aucun message d’erreur dans la console.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante :

*Impossible d’acquérir le verrou pour l’index : catalog_category_product.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
