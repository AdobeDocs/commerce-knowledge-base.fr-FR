---
title: 'MDVA-30357 : le plan de site généré par cron a une URL d’image incorrecte'
description: Le correctif MDVA-30357 corrige le problème en raison duquel une URL d’image incorrecte était créée par un plan de site généré par cron dans l’administrateur Commerce. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357 : le plan de site généré par cron a une URL d’image incorrecte

Le correctif MDVA-30357 corrige le problème en raison duquel une URL d’image incorrecte était créée par un plan de site généré par cron dans l’administrateur Commerce. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.6 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 à 2.4.0

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les plans de site générés par cron dans Adobe Commerce contiennent un chemin d’URL d’image incorrect.

<u>Étapes à reproduire</u>:

1. Dans l’administrateur Commerce, créez un site web, un magasin ou une vue de magasin.
1. Ajoutez au moins un produit à chaque magasin et au moins une image à chaque produit.
1. Activer **Génération du plan de site par planification** in **Administration** > **Magasins** > **Configuration** > **CATALOGUE** > **Plan du site XML** > **Paramètres de génération**.
1. Générez manuellement un plan du site pour l’une des deux boutiques dans **Administration** > **Marketing** > **Carte du site** utilisation d’un nom de plan de site comme &quot;*sitemap.xml*&quot;.
   * Renommez le fichier par un nom du type &quot;*manual\_sitemap.xml*&quot; ou copiez le contenu du fichier dans un éditeur de texte.
1. Générer le même plan de site par tâche cron `sitemap_generate`.
1. Comparer le plan de site généré manuellement *manual\_sitemap.xml*&quot; et le plan du site généré par cron &quot;*sitemap.xml*&quot;.

<u>Résultats attendus</u>:

L’URL du chemin d’accès de l’image du plan de site mise en cache est correcte.

<u>Résultats réels</u>:

Le plan de site généré par cron contient une URL de chemin d’image incorrecte. Si vous essayez d’ouvrir l’image à partir de &quot;*sitemap.xml*&quot;, un espace réservé par défaut s’affiche. Les URL de plan de site générées manuellement ne sont pas affectées par ce problème.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.

Pour en savoir plus sur les plans de site, reportez-vous à ces articles dans notre documentation destinée aux développeurs :

* [Ajout de robots de plan de site et de moteur de recherche](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Configuration et exécution de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Sécurisation de cron.php pour une exécution dans un navigateur](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
