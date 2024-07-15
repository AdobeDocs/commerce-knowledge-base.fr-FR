---
title: "ACSD-54060 : L’administrateur restreint ne peut pas enregistrer le produit s’il est enfant d’un autre produit"
description: Appliquez le correctif ACSD-54060 pour résoudre le problème Adobe Commerce en raison duquel un administrateur restreint ne peut pas enregistrer un produit s’il est un enfant d’un autre produit affecté à une portée différente.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060 : L’administrateur restreint ne peut pas enregistrer le produit s’il est enfant d’un autre produit.

Le correctif ACSD-54060 corrige le problème lorsqu’un administrateur restreint ne peut pas enregistrer un produit s’il est un enfant d’un autre produit affecté à une portée différente. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 est installé. L’ID de correctif est ACSD-54060. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un administrateur restreint ne peut pas enregistrer un produit s’il est enfant d’un autre produit affecté à une autre portée.

<u>Étapes à reproduire</u> :

1. Créez un site web supplémentaire.
1. Créez un produit simple et affectez-le aux deux sites web.
1. Créez un produit configurable avec le produit simple comme seule variante, et affectez le produit configurable uniquement au site web par défaut.
1. Créez un utilisateur administrateur restreint ayant accès uniquement au deuxième site web.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Essayez de modifier le nom simple du produit dans la deuxième portée du site web.

<u>Résultats attendus</u> :

L’administrateur restreint peut modifier le nom du produit.

<u>Résultats réels</u> :

Une erreur se produit : *D’autres autorisations sont nécessaires pour afficher cet élément*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
