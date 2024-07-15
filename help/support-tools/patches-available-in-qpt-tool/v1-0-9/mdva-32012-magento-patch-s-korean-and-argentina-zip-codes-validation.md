---
title: 'Correctif MDVA-32012 : validation des codes postaux S. Coréen et Argentine'
description: Le correctif MDVA-32012 résout le problème de non-validation des codes postaux argentins et sud-coréens en raison de modifications ou de variations dans les formats de codes postaux nationaux. Les codes postaux sud-coréens doivent maintenant comporter 5 chiffres, alors qu’ils ne le faisaient auparavant que pour 6 chiffres. Les codes postaux argentins peuvent être à la fois numériques et alphanumériques. Le correctif MDVA-32012 signifie que ces formats pour les valeurs de code postal seront validés pour ces pays. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.2.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Correctif MDVA-32012 : validation des codes postaux S. Coréen et Argentine

Le correctif MDVA-32012 résout le problème de non-validation des codes postaux argentins et sud-coréens en raison de modifications ou de variations dans les formats de codes postaux nationaux. Les codes postaux sud-coréens doivent maintenant comporter 5 chiffres, alors qu’ils ne le faisaient auparavant que pour 6 chiffres. Les codes postaux argentins peuvent être à la fois numériques et alphanumériques. Le correctif MDVA-32012 signifie que ces formats pour les valeurs de code postal seront validés pour ces pays. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.3.5.
* Le correctif est également compatible avec les versions d’Adobe Commerce suivantes : Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La saisie d’un code postal sud-coréen ou alphanumérique de l’Argentine à 5 chiffres génère un avertissement :

*Le code postal fourni semble non valide. Exemple : [1234 (si une adresse alphanumérique est saisie)] ou [123-456 (si une adresse sud-coréenne à 5 chiffres est saisie)]. Si vous pensez que c&#39;est le bon, vous pouvez ignorer cet avis.*

<u>Étapes à reproduire</u> :

1. Ouvrez le storefront.
1. Ajoutez un élément au panier.
1. Traitement du passage en caisse.
1. Ajoutez une nouvelle adresse avec la Corée du Sud pour le pays et saisissez un code postal à 5 chiffres, ou ajoutez une nouvelle adresse avec l’Argentine pour le pays, puis saisissez un code postal alphanumérique.
1. Essayez d’enregistrer.

<u>Résultats attendus</u> :

L’adresse doit être enregistrée sans avertissement.

<u>Résultats réels</u> :

L’enregistrement de l’adresse renvoie un avertissement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
