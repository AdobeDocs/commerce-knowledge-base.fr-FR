---
title: 'MDVA-44703 : les totaux des commandes dans le rapport Commandes sont mal calculés'
description: Le correctif MDVA-44703 corrige le problème en raison duquel les totaux des commandes dans le rapport Commandes sont mal calculés pour l’utilisateur administrateur restreint. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-44703. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: d8c31e47-ace6-4dba-a57c-941e722a6aad
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-44703 : Les totaux des commandes dans le rapport Commandes sont mal calculés.

Le correctif MDVA-44703 corrige le problème en raison duquel les totaux des commandes dans le rapport Commandes sont mal calculés pour l’utilisateur administrateur restreint. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-44703. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les totaux des commandes du rapport Commandes sont mal calculés pour l’utilisateur administrateur restreint.

<u>Étapes à reproduire</u> :

1. Créez un site web supplémentaire avec deux magasins.
1. Créez un utilisateur administrateur restreint ayant accès au nouveau site web uniquement.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Créez deux commandes avec des totaux différents, une pour chaque nouveau magasin.
1. Créez des factures pour les commandes.
1. Accédez à **Rapports** > **Ventes** et ouvrez **Rapport Commandes**.
1. Actualisez les statistiques.
1. Consultez le rapport pour chaque magasin.

<u>Résultats attendus</u> :

Les totaux des ventes correspondent au montant de la commande de chaque magasin.

<u>Résultats réels</u> :

Le total des ventes agrégées pour l’ensemble du site web s’affiche pour chaque magasin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
