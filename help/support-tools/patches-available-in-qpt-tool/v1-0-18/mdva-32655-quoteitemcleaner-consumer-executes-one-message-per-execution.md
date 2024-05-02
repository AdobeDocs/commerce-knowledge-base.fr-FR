---
title: 'MDVA-32655: le consommateur "entre guillemetsItemCleaner" exécute un message par exécution'
description: Le correctif MDVA-32655 corrige l’état du message "en cours" incorrect sur le message "terminé" correct pour le consommateur "quoteItemCleaner" après la suppression de plusieurs produits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 est installé. L’ID de correctif est 32655. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655 : le consommateur &quot;quoteItemCleaner&quot; exécute un message par exécution

Le correctif MDVA-32655 corrige l’état du message &quot;en cours&quot; incorrect sur le message &quot;terminé&quot; correct pour le consommateur `quoteItemCleaner` après la suppression de plusieurs produits. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.18 est installée. L’ID de correctif est 32655. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La variable `quoteItemCleaner` consumer n&#39;exécute qu&#39;un seul message sur chaque exécution.

<u>Étapes à reproduire</u>:

1. Vérifiez les `queue_message_status` de la base de données et assurez-vous que tous les messages de file d’attente existants sont à l’état &quot;Terminé&quot; (ID d’état 4).
1. Arrêtez l’exécution automatique cron Adobe Commerce.
1. Créez deux ou trois produits simples.
1. Supprimez en masse ces trois produits simples.
1. Dans le `queue_message_status` vous voyez qu’il y a trois nouveaux enregistrements pour le `catalog_product_removed_queue` rubrique avec ID d’état 2 (nouvel enregistrement).
1. Exécutez la commande suivante pour traiter ces en attente `catalog_product_removed_queue` messages :

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Résultats attendus</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Tous les `catalog_product_removed_queue` les statuts des messages sont mis à jour pour se terminer (ID=4).

<u>Résultats réels</u>:

Un seul enregistrement sur trois est mis à jour vers l’état &quot;Terminé&quot; (ID = 4). L’état des deux autres messages est ID d’état = 3 (en cours). Un journal des logs est généré avec les messages de file d’attente non traités.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
