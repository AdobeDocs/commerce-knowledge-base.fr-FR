---
title: 'ACSD-57854: *La réponse GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories'
description: Appliquez le correctif ACSD-57854 pour résoudre le problème Adobe Commerce en raison duquel la réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854 : *La réponse GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.

Le correctif ACSD-57854 corrige le problème en raison duquel la réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.48 est installé. L’ID de correctif est ACSD-57854. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.

<u>Étapes à reproduire</u> :

1. Créez deux catégories.
1. Créez un produit (Tester le produit d’Adobe) et affectez-le aux deux catégories.
1. Désactivez l&#39;une des catégories qui a été créée.
1. Utilisez les produits *GraphQL* pour rechercher le produit.
1. Vérifiez la liste des catégories de produits dans la réponse *GraphQL*.

<u>Résultats attendus</u> :

Les catégories désactivées ne sont pas répertoriées dans la réponse *GraphQL*.

<u>Résultats réels</u> :

Les catégories désactivées sont répertoriées dans la réponse d’agrégation de catégories *GraphQL*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
