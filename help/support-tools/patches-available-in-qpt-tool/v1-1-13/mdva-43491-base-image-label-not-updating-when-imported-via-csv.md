---
title: '''MDVA-43491 : Libellé de l''image de base non mis à jour lors d''un import via CSV'''
description: Le correctif MDVA-43491 corrige le problème en raison duquel le `base_image_label` ne se met pas à jour lors d’un import via un fichier CSV pour un site web multi-magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-43491. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491 : Libellé de l’image de base non mis à jour lors d’un import via CSV

Le correctif MDVA-43491 corrige le problème où `base_image_label` ne se met pas à jour lors d’un import via un fichier CSV pour un site web multi-magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-43491. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`base_image_label` ne se met pas à jour lors d’un import à l’aide d’un fichier CSV pour un site web multi-magasin.

<u>Conditions préalables</u> :

Un ou plusieurs sites web, magasins et vues de magasin qui ne sont pas par défaut.

<u>Étapes à reproduire</u> :

1. Créez un produit.

   * Téléchargez une image.
   * Affectez le produit aux sites web nouvellement créés.

1. Exportez le produit au format CSV.
1. Mettez à jour `base_image_label` pour chaque vue de magasin en dupliquant la ligne par défaut du fichier CSV.
1. Importez le fichier CSV. Il mettra correctement à jour les libellés de chaque magasin, qui peuvent être vérifiés sous l’onglet **Images et vidéos** de la page de modification du produit.
1. Exportez à nouveau le fichier CSV et mettez à jour la colonne `base_image_label` avec des valeurs différentes.
1. Importez à nouveau le fichier CSV.
1. Ouvrez le produit dans Admin et vérifiez si le libellé a été mis à jour pour chaque vue de magasin.

<u>Résultats attendus</u> :

Le texte de remplacement (libellé de l’image) est mis à jour avec la valeur spécifique au magasin, conformément au fichier CSV.

<u>Résultats réels</u> :

Le texte de remplacement (libellé de l’image) n’est pas mis à jour avec la valeur `base_image_label` dans le fichier CSV.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
