---
title: 'MDVA-23764 Correctif du Magento : erreur lors du chargement des blocs dynamiques'
description: Le correctif du Magento MDVA-23764 corrige le bogue dans
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# MDVA-23764 Correctif du Magento : erreur lors du chargement des blocs dynamiques

Le correctif du Magento MDVA-23764 corrige le bogue dans

```php
JsFooterPlugin.php
```

qui affecte l&#39;affichage des blocs dynamiques. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.13 est installée. Veuillez noter que le problème a été corrigé dans Magento 2.3.5.

## Produits et versions concernés

**Le correctif est créé pour la version du Magento :** Magento Commerce Cloud 2.3.3.

**Compatible avec les versions de Magento :** Magento Commerce et Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire :</u>

Essayez de charger une URL qui ressemble à ceci : https://\[domaine magento\]/banner/ajax/load/.

<u>Résultat réel :</u>

Une erreur similaire à la suivante est générée : *TypeError non intercepté : strpos() s’attend à ce que le paramètre 1 soit une chaîne, null fourni dans... (ligne de code).* .

<u>Résultat attendu :</u>

L’URL est chargée sans erreur.

## Appliquer le correctif

Pour savoir comment appliquer un correctif QPT, utilisez les liens suivants en fonction de votre produit Magento :

* Magento Commerce : DevDocs [Application de correctifs à l’aide de l’outil Correctifs de qualité](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud : DevDocs [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Vérifiez si le correctif est disponible pour votre problème de Magento à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
