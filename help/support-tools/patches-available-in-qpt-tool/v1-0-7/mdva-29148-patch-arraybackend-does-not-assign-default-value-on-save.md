---
title: 'MDVA-29148 : ArrayBackend n’affecte pas de valeur par défaut lors de l’enregistrement'
description: Le correctif MDVA-29148 résout le problème où "\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend" n’affecte pas la valeur par défaut lors de l’enregistrement. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148 : ArrayBackend n’attribue pas de valeur par défaut lors de l’enregistrement.

Le correctif MDVA-29148 résout le problème où `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` n’affecte pas la valeur par défaut lors de l’enregistrement. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.3-p1.

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un produit est créé via un script d’importation ou l’API REST, la valeur par défaut n’est pas affectée aux attributs qui utilisent le modèle principal `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` et qui possèdent une valeur par défaut.

<u>Étapes à reproduire</u> :

1. Créez un nouvel attribut global qui utilise le modèle principal `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` et une valeur par défaut non vide.
1. Utilisez l’API REST pour créer un produit.
1. Récupérez ce nouveau produit à partir de l’API REST et vérifiez que l’attribut n’est pas présent dans les attributs personnalisés du produit.

<u>Résultats attendus</u> :

La valeur par défaut de l’attribut personnalisé a été enregistrée dans l’attribut product .

<u>Résultats réels</u> :

La valeur par défaut de l’attribut personnalisé n’a pas été enregistrée dans l’attribut product .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
