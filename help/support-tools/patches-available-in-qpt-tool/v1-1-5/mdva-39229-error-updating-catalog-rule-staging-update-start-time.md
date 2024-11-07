---
title: 'MDVA-39229 : Erreur après la mise à jour de l’heure de début de mise à jour de la règle de catalogue intermédiaire'
description: Le correctif MDVA-39229 corrige le problème qui entraînait une erreur des utilisateurs après la mise à jour de l’heure de début de la mise à jour de l’évaluation de la règle de catalogue. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 est installé. L’ID de correctif est MDVA-39229. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229 : Erreur après la mise à jour de l’heure de début de mise à jour de la règle de catalogue intermédiaire

Le correctif MDVA-39229 corrige le problème qui entraînait une erreur des utilisateurs après la mise à jour de l’heure de début de la mise à jour de l’évaluation de la règle de catalogue. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 est installé. L’ID de correctif est MDVA-39229. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs reçoivent une erreur après la mise à jour de l’heure de début de la mise à jour de l’évaluation des règles du catalogue.

<u>Étapes à reproduire</u> :

1. Créez une règle de prix de catalogue.
1. Créez et exécutez toute mise à jour d’évaluation.
1. Exécutez la requête et vérifiez que l’indicateur d’évaluation a été créé.


   `select * from flag;`


1. Créez une mise à jour d’évaluation qui démarrera au bout de cinq minutes.
1. Ouvrez **Contenu** > **Évaluation** > **Tableau de bord** > **Nouvelle mise à jour** et retardez l’heure de début d’une minute.
1. Attends six minutes.
1. Exécutez cron.

<u>Résultats attendus</u> :

L’heure de début de la mise à jour est modifiée et la mise à jour est appliquée. L’ancienne mise à jour est supprimée de la table `staging_update`.

<u>Résultats réels</u> :

Les utilisateurs reçoivent l’erreur suivante :

*report.ERROR : Cron Job staging_synchronize_entities_period a une erreur : la mise à jour active ne peut pas être supprimée.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
