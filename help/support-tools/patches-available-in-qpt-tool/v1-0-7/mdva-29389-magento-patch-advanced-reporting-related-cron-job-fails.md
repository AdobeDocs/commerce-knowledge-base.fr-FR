---
title: 'MDVA-29389 : échec de la tâche cron liée aux rapports avancés'
description: '"Le correctif MDVA-29389 corrige le problème en raison duquel avec le reporting avancé, où le cronjob "analytics_collect_data" disait : "*Le port doit être configuré dans un paramètre d’hôte (comme localhost:3306)*". Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. L’ID de correctif est MDVA-29389. Le problème a été corrigé dans Adobe Commerce 2.4.2."'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389 : Échec de la tâche cron liée aux rapports avancés

Le correctif MDVA-29389 corrige le problème en raison duquel, avec le reporting avancé, la fonction `analytics_collect_data` cronjob dit : &quot;*Le port doit être configuré dans le paramètre hôte (comme localhost:3306).*&quot;. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.7 est installée. L’ID de correctif est MDVA-29389. Le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4.

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Dans votre instance Adobe Commerce, activez la création de rapports avancés.
1. Exécutez la requête suivante pour insérer la valeur analytics/general/token dans la base de données :

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Ouvrez le fichier env.php et ajoutez le port au paramètre hôte dans la configuration DB au format suivant : `'host' => 'hostname:port',`
1. Effacez le cache.
1. Exécutez le `analytics_collect_data` tâche cron.

<u>Résultats attendus</u>:

La variable `analytics_collect_data` s’exécute correctement lors de l’utilisation d’un port par défaut ou non par défaut pour se connecter à MySQL dans env.php.

<u>Résultats réels</u>:

La variable `analytics_collect_data` la tâche renvoie une erreur &quot;*Le port doit être configuré dans le paramètre hôte (comme localhost:3306).*&quot; lors de l’utilisation d’un port autre que le port par défaut pour se connecter à MySQL dans env.php.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
