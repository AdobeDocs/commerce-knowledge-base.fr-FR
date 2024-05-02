---
title: 'Correctif MDVA-13203 : erreur 503 - page d’accueil post full reindex'
description: 'Le correctif Adobe Commerce MDVA-13203 corrige le problème où votre site affiche une page de maintenance et où il y a *CRITICAL: SQLSTATE\[23000\] : des erreurs de violation de contrainte d’intégrité* dans le `system.log`. L’ID de correctif est MDVA-13203. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 est installé.'
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Correctif MDVA-13203 : erreur 503 - page d’accueil post reindex full

Le correctif Adobe Commerce MDVA-13203 corrige le problème en raison duquel votre site affiche une page de maintenance. *CRITIQUE : SQLSTATE\[23000\] : violation de contrainte d’intégrité* Erreurs dans le `system.log`. L’ID de correctif est MDVA-13203. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.13 est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.2.4.

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire :</u>

1. Accédez à l’URL concernée.
1. La page de maintenance s’affiche.
1. Vérifiez que le site n’est pas en état de maintenance via SSH :
   <pre> Maintenance bin/magento:status : le mode de maintenance n'est pas actif Liste des adresses IP exemptées : aucune</pre>
1. Regarder `system.log`:

<pre>grep critical -i var/log/system.log |tail [2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: Violation de contrainte d’intégrité : 1062 Entrée en double '4613' pour la clé 'PRINCIPAL', la requête était : INSERT INTO `search_tmp_5b8ebb4e994da5_88027289` (`entity_id`,) VALEURS (?, ?),... (?, ?), (?, ?) [] [2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: Violation de contrainte d’intégrité : 1062 Entrée en double '4613' pour la clé 'PRINCIPAL', la requête était : INSERT INTO `search_tmp_5b8ebb51579943_52333638` (`entity_id,`score`). ..,(?, ?) [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Violation de contrainte d’intégrité : 1062 Entrée en double '1350' pour la clé 'PRINCIPAL', la requête était : INSERT INTO `search_tmp_5b8ebb6b7028f4_68065024` ( score`) VALEURS (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000] : violation de contrainte d’intégrité : 1062 Entrée en double '1350' pour la clé 'PRINCIPAL', la requête était : INSERT INTO `search_tmp_5b8ebb6b7885a9_23360993` (`entity_id`, score`) VALEURS (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] [] date Tue 4 septembre 17:06:11 UTC 2018</pre>

<u>Résultats attendus :</u> Vous devriez voir le site.

<u>Résultats réels :</u> La page de maintenance s’affiche en raison de problèmes de cohérence de la base de données.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
