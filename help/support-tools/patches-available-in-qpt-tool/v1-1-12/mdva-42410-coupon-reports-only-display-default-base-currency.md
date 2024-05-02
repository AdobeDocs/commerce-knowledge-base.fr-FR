---
title: 'MDVA-42410 : les rapports Coupon affichent uniquement la devise de base par défaut'
description: Le correctif MDVA-42410 corrige le problème en raison duquel les rapports de coupon n’affichent que la devise de base. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-42410. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410 : Les rapports Coupon affichent uniquement la devise de base par défaut

Le correctif MDVA-42410 corrige le problème en raison duquel les rapports de coupon n’affichent que la devise de base. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.12 est installée. L’ID de correctif est MDVA-42410. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les rapports Coupon affichent uniquement la devise de base par défaut.

<u>Étapes à reproduire</u>:

1. Créez un site Web, un magasin et une vue de magasin supplémentaires.
1. Définissez une devise différente pour ce nouveau site web. Par exemple, l’euro.
1. Accédez à **Magasins** > **Taux de change** et configurez les taux de devise sur **Euro**.
1. Créez un **Règle de prix du panier** avec un coupon spécifique - **Test**.
1. Accédez à l’interface frontale et passez une commande à l’aide de la fonction **Test** coupon sur le nouveau site web.
1. Accédez à **Rapports** > **Ventes** > **Coupons**.
1. Sélectionnez le nouveau site web dans la liste déroulante Portée .
1. Actualisez les statistiques et exécutez des rapports.

<u>Résultats attendus</u>:

Les rapports Coupon affichent la devise du nouveau site web en euro.

<u>Résultats réels</u>:

La devise de base par défaut (le dollar américain, dans ce cas) est utilisée dans les rapports sur les coupons pour le nouveau site web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
