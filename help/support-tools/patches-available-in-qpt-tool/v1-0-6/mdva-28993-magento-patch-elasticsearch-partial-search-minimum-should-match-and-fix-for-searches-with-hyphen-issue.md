---
title: '''MDVA-28993 : recherche partielle Elasticsearch, "le minimum doit correspondre" et correction du problème "recherches avec trait d’union"'
description: Le correctif MDVA-28993 met en oeuvre la fonctionnalité "Minimum should match" (Minimum doit correspondre) et la recherche partielle pour le moteur Elasticsearch, et résout les problèmes liés aux tirets dans les requêtes de recherche. Le correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 est installé.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993 : recherche partielle Elasticsearch, &quot;le minimum doit correspondre&quot; et correctif pour le problème &quot;recherches avec trait d’union&quot;

Le correctif MDVA-28993 met en oeuvre la fonctionnalité &quot;Minimum should match&quot; (Minimum doit correspondre) et la recherche partielle pour le moteur Elasticsearch, et résout les problèmes liés aux tirets dans les requêtes de recherche. Le correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 est installé.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.4

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site/Adobe Commerce sur l’infrastructure cloud 2.3.4-2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.


## Problème

Lors de l’utilisation d’Elasticsearch 6 pour la recherche d’un SKU contenant un trait d’union (-), la recherche renvoie trop de résultats.

<u>Étapes à reproduire :</u>

1. Allez à la vitrine.

1. Dans la barre de recherche, saisissez une chaîne contenant un trait d’union, par exemple &quot;WS-M-Blue&quot;.

<u>Résultat attendu :</u>

Renvoie uniquement WS-M-Blue.

<u>Résultat réel :</u>

Renvoie tous les SKU commençant par &quot;WS&quot;.

## Détails du correctif

Le correctif MDVA-28993 contient les correctifs et améliorations suivants :

* met en oeuvre la nouvelle fonctionnalité &quot;Minimum doit correspondre&quot; et la recherche partielle pour le moteur Elasticsearch. Pour plus d’informations sur la configuration, voir [Configuration de la recherche catalogue](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) dans notre guide d’utilisation.
* recherche partielle d’Elasticsearch
* corrige le problème &quot;recherches avec trait d’union&quot; décrit ci-dessus.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
