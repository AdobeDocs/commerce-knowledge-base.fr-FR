---
title: "ACSD-51114 : les produits aléatoires ont disparu des catalogues volumineux lorsque l’indexation asynchrone est activée"
description: Appliquez le correctif ACSD-51114 pour résoudre le problème Adobe Commerce Les produits aléatoires disparaissent des catalogues volumineux lorsque l’indexation asynchrone est activée.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114 : les produits aléatoires disparaissent des catalogues volumineux lorsque l’indexation asynchrone est activée

>[!NOTE]
>
>Ce correctif est obsolète.

Le correctif ACSD-5114 corrige le problème lié à la disparition des produits aléatoires des catalogues volumineux lorsque l’indexation asynchrone est activée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.30 est installée. L’ID de correctif est ACSD-51114. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur le [[!DNL Quality Patches Tool]: Recherchez la page des correctifs]. Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits aléatoires disparaissaient des catalogues volumineux lorsque l’indexation asynchrone était activée.

<u>Étapes à reproduire</u>:

1. Créez un ensemble de 10 produits.
1. Définir tous les indexeurs sur **[!UICONTROL Update on Save]** mode .
1. Créez une catégorie et affectez-lui tous les produits.
1. Désactivez tous les produits.
1. Ouvrez la catégorie et vérifiez qu’il n’y a aucun produit.
1. Définir tous les indexeurs sur **[!UICONTROL Update on Schedule]** mode .
1. Définissez la variable `DEFAULT_BATCH_SIZE` à 2 pouces  `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Activez les produits dans l’ordre suivant : 1er, 9e, 2e, 5e, 10e, 3e.
1. Exécutez la commande cron.
1. Ouvrez à nouveau la catégorie.

<u>Résultats attendus</u>:

Tous les produits activés s’affichent.

<u>Résultats réels</u>:

Tous les produits activés ne s’affichent pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
