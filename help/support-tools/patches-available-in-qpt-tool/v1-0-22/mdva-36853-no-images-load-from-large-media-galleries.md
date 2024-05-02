---
title: 'MDVA-36853 : Aucune image ne se charge depuis les grandes galeries de médias'
description: Le correctif MDVA-36853 corrige le problème lorsqu’aucune image ne se charge, car le widget de galerie multimédia du créateur de pages ne se charge pas lorsque vous avez un répertoire multimédia volumineux.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853 : aucune image n’est chargée à partir des galeries de médias volumineuses

Le correctif MDVA-36853 corrige le problème lorsqu’aucune image ne se charge, car le widget de galerie multimédia du créateur de pages ne se charge pas lorsque vous avez un répertoire multimédia volumineux.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.22 est installée. L’ID de correctif est MDVA-36853. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Définir **Activer la vieille galerie de médias** = *Oui* in **Admin > Magasins > Configuration > Avancé > Système > Galerie de médias**.
1. Accédez à **Contenu > Blocs** et créez un bloc CMS ou modifiez un bloc CMS existant.
1. Cliquez sur le bouton **Modifier avec Pagebuilder** bouton .
1. Ajoutez un élément multimédia.
1. Cliquez sur le bouton **Sélectionner dans la galerie** bouton .

<u>Résultats attendus</u>:

Le widget de la galerie multimédia et les images de la galerie multimédia se chargent tous les deux, comme prévu.

<u>Résultats réels</u>:

Le widget de la galerie multimédia et les images de la galerie multimédia ne se chargent pas lorsque vous disposez d’une grande `pub/media/catalog/product/cache/` répertoire .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants, en fonction de votre produit Adobe Commerce :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
