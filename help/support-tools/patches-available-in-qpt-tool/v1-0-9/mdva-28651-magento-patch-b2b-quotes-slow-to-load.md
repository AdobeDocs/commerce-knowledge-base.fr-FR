---
title: 'MDVA-28651 : B2B - guillemets lents à charger'
description: Le correctif MDVA-28651 résout le problème où plusieurs problèmes de performances se produisent avec les guillemets de chargement. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 est installé. Veuillez noter que le problème a été planifié pour être corrigé dans Adobe Commerce version 2.4.2.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651 : B2B - guillemets lents à charger

Le correctif MDVA-28651 résout le problème où plusieurs problèmes de performances se produisent avec les guillemets de chargement. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 est installé. Veuillez noter que le problème a été planifié pour être corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.4.
* Le correctif est également compatible avec les versions d’Adobe Commerce suivantes : Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0-2.3.5-p1, 2.4.0 et 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problèmes de performances sur la page de liste des devis des clients :

* double chargement de la liste de guillemets : d’abord avec une page entière, puis avec la requête Ajax.
* boucle de chargement de chacun des guillemets du module externe.
* double chargement des éléments de guillemet lorsque le guillemet a été converti en instantané.

<u>Étapes à reproduire</u>

1. Avoir plus de 40 guillemets attribués à un client.
1. Connectez-vous et parcourez les **Mes citations** page.

<u>Résultat réel</u>

Le temps de réponse pour charger complètement le contenu de la variable **Mes citations** page (chargement de la page + données affichées dans la grille) est environ 45 secondes.

<u>Résultat attendu</u>

Le temps de réponse pour charger complètement le contenu de la variable **Mes citations** doit être inférieure à 45 secondes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
