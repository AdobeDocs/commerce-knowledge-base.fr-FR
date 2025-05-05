---
title: "MDVA-31763 : les règles de prix du catalogue sont restaurées jusqu’à la réindexation manuelle"
description: Le correctif MDVA-31763 résout le problème en raison duquel les règles de prix du catalogue sont annulées jusqu’à la réindexation manuelle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 est installé. L’ID de correctif est MDVA-31763. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763 : les règles de prix du catalogue sont restaurées jusqu’à la réindexation manuelle.

Le correctif MDVA-31763 résout le problème en raison duquel les règles de prix du catalogue sont annulées jusqu’à la réindexation manuelle. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 est installé. L’ID de correctif est MDVA-31763. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque l’indexeur partiel `catalogrule_product` est exécuté sur des produits configurables, les règles du catalogue disparaissent.

<u>Étapes à reproduire</u> :

1. Connectez-vous au serveur principal Admin.
1. Accédez à **Magasins** > **Attributs** > **Produit** et recherchez l’attribut &quot;manufacturer&quot;.
   * Ajoutez quelques options et définissez &quot;Utiliser pour les conditions des règles de promotion&quot; sur *Oui*.
1. Accédez à **Magasins** > **Attributs** > **Visionneuses d’attributs**.
   * Sélectionnez le jeu d’attributs par défaut et ajoutez-lui l’attribut &quot;manufacturer&quot;.
1. Créez un produit configurable avec quelques variantes.
1. Définissez la valeur d’attribut &quot;manufacturer&quot; pour le produit configurable créé précédemment.
1. Créer des règles de catalogue :
   * Actif = Oui
   * Sites web = site web principal
   * Groupes clients = NON CONNECTÉ
   * Conditions : manufacturer = \&lt;valeur sélectionnée pour le produit configurable>
   * Actions : Toute remise
1. Effectuez un index complet.
1. Vérifiez le prix du produit sur PDP et assurez-vous que le prix est correct.
1. Mettez à jour l’attribut &quot;weight&quot; du produit configurable créé.
1. Vérifiez le prix du produit sur PDP.

<u>Résultats attendus</u> :

Les règles de prix du catalogue définies sur les produits configurables ne sont pas supprimées lors d’une réindexation partielle.

<u>Résultats réels</u> :

Les règles de prix du catalogue définies sur les produits configurables disparaissent lors d’une réindexation partielle.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
