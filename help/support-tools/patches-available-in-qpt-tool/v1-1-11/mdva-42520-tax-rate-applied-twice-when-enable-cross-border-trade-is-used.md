---
title: 'MDVA-42520 : Taux de taxe appliqué deux fois lorsque "Activer le commerce transfrontalier" est utilisé'
description: Le correctif MDVA-42520 corrige le problème où le taux d'imposition est appliqué deux fois lorsque l'option **Activer le commerce transfrontalier** est utilisée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé. L’ID de correctif est MDVA-42520. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520 : Taux d&#39;imposition appliqué deux fois lorsque &quot;Activer le commerce transfrontalier&quot; est utilisé

Le correctif MDVA-42520 corrige le problème où le taux d&#39;imposition est appliqué deux fois lorsque le **Activer le commerce transfrontalier** est utilisé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 est installé. L’ID de correctif est MDVA-42520. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de taxe est appliqué deux fois lorsque l’option **Activer le commerce transfrontalier** est utilisée.

<u>Étapes à reproduire</u> :

1. Activez **Société**, **Catalogue partagé** et **Devis**
1. Paramétrez les taxes en fonction de la capture d&#39;écran. Assurez-vous d’activer l’option **Commerce transfrontalier**.

   ![Paramètres de taxe](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. Créer un taux d&#39;imposition pour l&#39;Allemagne (10%).
1. Créez une règle fiscale pour appliquer le taux de taxe.
1. Créez une société et un catalogue partagé personnalisé.
1. Créez un produit au prix de 100 et incluez-le dans le catalogue partagé personnalisé avec une remise de 20 %.
1. Créer un client avec une adresse allemande et l’affecter à la société
1. Ajoutez 10 produits à la carte en tant que client.
1. Accédez au panier et demandez un devis.
1. Ouvrez ce guillemet sur le serveur principal et essayez d’ajouter une remise supplémentaire de 10 %.

<u>Résultats attendus</u> :

Sous-total des citations (y compris les taxes) et Total général des citations (y compris les taxes) = 720 $

<u>Résultats réels</u> :

Sous-total des citations (y compris les taxes) et Total général des citations (y compris les taxes) = 649,50 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
