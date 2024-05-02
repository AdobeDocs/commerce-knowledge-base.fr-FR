---
title: 'MDVA-21095 : INSERTION DANS "search_tmp.." ne se termine jamais après la mise à jour de masse des attributs'
description: Le correctif MDVA-21095 corrige le problème lorsqu’une requête "INSERT INTO" "search\_tmp.." ne se termine jamais après une mise à jour d’attribut de masse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MDVA-21095. Veuillez noter qu’il n’existe actuellement aucun plan pour résoudre ce problème dans les versions futures.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095 : INSERTION DANS &quot;search_tmp...&quot; ne se termine jamais après la mise à jour massive des attributs.

Le correctif MDVA-21095 corrige le problème lorsqu’une requête `INSERT INTO` &quot;search\_tmp...&quot; ne se termine jamais après la mise à jour d’un attribut de masse. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.20 est installée. L’ID de correctif est MDVA-21095. Veuillez noter qu’il n’existe actuellement aucun plan pour résoudre ce problème dans les versions futures.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`INSERT INTO` &quot;search\_tmp...&quot; ne se termine jamais après la mise à jour d’un attribut de masse.

<u>Étape à reproduire</u>:

Effectuez une mise à jour des valeurs d’attribut de masse avec ~30 000 éléments.

<u>Résultats attendus</u>:

Le processus de réindexation se termine normalement, comme prévu.

<u>Résultats réels</u>:

Le processus de réindexation s’achève, mais de nombreuses requêtes `INSERT INTO` &quot;search\_tmp..&quot; démarrez jusqu’à ce que le serveur atteigne la valeur `pm.max_children` la valeur du paramètre et le fichier PHP-fpm disparaissent, et ces événements se reproduisent constamment même après le redémarrage de MySQL et l’arrêt des processus.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
