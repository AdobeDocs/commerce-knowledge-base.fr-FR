---
title: 'Correctif MDVA-28409 : panne du serveur web Adobe Commerce - mémoire insuffisante'
description: Le correctif MDVA-28409 résout le problème en raison duquel la tâche cron de suppression des guillemets s’arrêtait en raison du traitement d’un grand nombre d’éléments. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 est installé.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Correctif MDVA-28409 : panne du serveur web Adobe Commerce - mémoire insuffisante

Le correctif MDVA-28409 résout le problème en raison duquel la tâche cron de suppression des guillemets s’arrêtait en raison du traitement d’un grand nombre d’éléments. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 est installé.

## Produits et versions concernés

Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le problème est que la tâche cron est à court de mémoire en raison de la quantité de données que la tâche tente de traiter. Les symptômes de ce problème incluent des performances lentes en raison de l’utilisation élevée du disque par MySQL et de la faible mémoire du serveur web.

<u>Étapes à reproduire :</u>

Pour vérifier si une tâche cron ne peut pas supprimer les guillemets obsolètes, exécutez la requête suivante :

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Résultat attendu :</u>

L’état de `sales_clean_quotes` la tâche cron doit `success`.

<u>Résultat réel :</u>

L’état de `sales_clean_quotes` la tâche cron est `running` ou `error`.

Une autre manière de confirmer qu’il existe une tâche cron qui ne peut pas supprimer les guillemets obsolètes consiste à mapper la sortie de la requête à partir de **Étape 1** (`executed_at`) par rapport aux horodatages des erreurs de mémoire dans `/var/log/cron.log`. Si une tâche cron ne peut pas traiter la quantité de données, un message similaire à celui-ci peut s’afficher :

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
