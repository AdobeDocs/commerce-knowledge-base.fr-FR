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

# ACSD-57854 : *GraphQL* La réponse contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.

Le correctif ACSD-57854 corrige le problème en raison duquel la variable *GraphQL* La réponse contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.48 est installée. L’ID de correctif est ACSD-57854. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*GraphQL* La réponse contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.

<u>Étapes à reproduire</u>:

1. Créez deux catégories.
1. Créez un produit (Tester le produit d’Adobe) et affectez-le aux deux catégories.
1. Désactivez l&#39;une des catégories qui a été créée.
1. Utiliser des produits *GraphQL* pour rechercher le produit.
1. Vérifiez la liste des catégories de produits dans la variable *GraphQL* réponse.

<u>Résultats attendus</u>:

Les catégories désactivées ne sont pas répertoriées dans la *GraphQL* réponse.

<u>Résultats réels</u>:

Les catégories désactivées sont répertoriées dans l’agrégation des catégories. *GraphQL* réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
