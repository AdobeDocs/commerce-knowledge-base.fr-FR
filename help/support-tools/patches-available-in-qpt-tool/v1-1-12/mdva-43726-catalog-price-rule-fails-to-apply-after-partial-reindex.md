---
title: 'MDVA-43726 : la règle de prix du catalogue ne s’applique pas après la réindexation partielle'
description: Le correctif MDVA-43726 corrige le problème en raison duquel la règle de prix du catalogue basée sur la correspondance des attributs au niveau du magasin ne s’appliquait pas après une réindexation partielle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-43726. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726 : la règle de prix du catalogue ne s’applique pas après la réindexation partielle.

Le correctif MDVA-43726 corrige le problème en raison duquel la règle de prix du catalogue basée sur la correspondance des attributs au niveau du magasin ne s’appliquait pas après une réindexation partielle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-43726. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de prix du catalogue basée sur la correspondance des attributs au niveau du magasin ne s’applique pas après une réindexation partielle.

<u>Étapes à reproduire</u> :

1. Définissez le mode indexeur pour qu’il s’exécute selon le calendrier.
1. Créez deux attributs de produit configurables. Par exemple : couleur (échantillon visuel) et taille (échantillon de texte).
1. Créez un produit configurable à l’aide des deux attributs créés à l’étape 2.
1. Après avoir créé les produits, créez un attribut de type **Oui/Non** et rendez-le visible dans les conditions de la règle.
1. Ajoutez cet attribut au jeu d’attributs par défaut.
1. Créez une règle de prix de catalogue à appliquer lorsque cet attribut est défini sur **Oui**.
1. Ouvrez l’un des produits simples liés au produit configurable.
1. Modifiez la portée pour stocker la vue et mettre à jour la valeur de l’attribut sur **Yes**.
1. Exécutez le `CRON` et vérifiez le prix sur le front-end.
1. Exécutez une réindexation complète. Encore une fois, vérifiez le prix à la frontale.
1. Mettez à jour la catégorie de produits configurable.
1. Exécutez le `CRON` et vérifiez à nouveau le prix sur le front-end.

<u>Résultats attendus</u> :

La règle de catalogue s’applique correctement sans réindexation complète à l’aide d’indexeurs incrémentiels.

<u>Résultats réels</u> :

La règle de catalogue ne s’applique pas sans effectuer une réindexation complète.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
