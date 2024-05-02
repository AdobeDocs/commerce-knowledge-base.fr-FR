---
title: 'MDVA-31590 : impossible de mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL'
description: Le correctif MDVA-31590 résout le problème où les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 est installé. L’ID de correctif est MDVA-31590. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590 : impossible de mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL

Le correctif MDVA-31590 résout le problème où les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.3 est installée. L’ID de correctif est MDVA-31590. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide de MySQL async.

<u>Étapes à reproduire</u>:

1. Sur la grille de produit du serveur principal, effectuez une action de masse pour mettre à jour les valeurs d’attribut de quelques produits.
   * Vérifiez les produits et sélectionnez **Mise à jour des attributs** dans la liste déroulante Actions .
1. Définissez des valeurs pour les attributs requis, affectez des produits aux sites web et enregistrez.
1. Une fois la page rechargée, un message similaire à celui-ci s’affiche :
   *Tâche &quot;Mise à jour des attributs pour N produits sélectionnés&quot; : 1 élément(s) a été planifié pour une mise à jour.*
1. Patientez quelques secondes et rechargez la page principale.

<u>Résultats attendus</u>:

1. La page affiche un message de mise à jour réussi, tel que : *1 élément(s) a été mis à jour.*
1. Les valeurs d’attribut pour les produits associés sont mises à jour.
1. Dans DB, de nouveaux enregistrements sont créés dans les deux `magento_bulk` table et `magento_operation` table (opérations liées au lot).
1. De nouveaux enregistrements sont créés dans le `queue_message` table (liée aux files d’attente) `product_action_attribute.update` et/ou `product_action_attribute.website.update`).
1. `queue_message_status` ont des enregistrements avec le statut &quot;4&quot;.
1. Aucune erreur n’est survenue dans `system.log`.

<u>Résultats réels</u>:

1. La page affiche toujours un message du type :
   *Tâche &quot;Mise à jour des attributs pour N produits sélectionnés&quot; : 1 élément(s) a été planifié pour une mise à jour.*
1. Les valeurs d’attribut des produits sont mises à jour.
1. Un nouvel enregistrement est créé dans `message_bulk` , mais il n’existe aucun enregistrement associé dans `magento_operation` table.
1. De nouveaux enregistrements sont créés dans `queue_message` et `queue_message_status` des tables.
1. `queue_message_status` La table contient un enregistrement avec un état d’erreur (valeur d’état &quot;6&quot;).
1. `system.log` contient une erreur similaire à celle-ci :
   *main.CRITICAL : le message a été rejeté : SQLSTATE[23 000]: violation de contrainte d’intégrité : 1048 La colonne &#39;operation_key&#39; ne peut pas être nulle, la requête était : INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALEURS (?, ?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
