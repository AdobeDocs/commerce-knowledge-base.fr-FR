---
title: 'MDVA-41236 : impossible de créer ou de modifier des mises à jour planifiées existantes pour le produit'
description: Le correctif MDVA-41236 corrige le problème qui empêchait les utilisateurs de créer ou de modifier des mises à jour planifiées existantes pour le produit si la "Date de fin" avait été supprimée précédemment. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 est installé. L’ID de correctif est MDVA-41236. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236 : impossible de créer ou de modifier des mises à jour planifiées existantes pour le produit.

Le correctif MDVA-41236 corrige le problème qui empêchait les utilisateurs de créer ou de modifier des mises à jour planifiées existantes pour le produit si la &quot;Date de fin&quot; avait été supprimée précédemment. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 est installé. L’ID de correctif est MDVA-41236. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas créer de calendriers ou modifier des calendriers existants pour les produits si la &quot;Date de fin&quot; a été supprimée précédemment.

<u>Étapes à reproduire</u> :

1. Créez un produit dont l’état est défini sur *disable*.
1. Ajoutez une mise à jour planifiée pour activer ce produit.
   * Ajoutez des dates de début et de fin futures.
1. Modifiez la mise à jour planifiée en supprimant la **Date de fin**.
1. Modifiez à nouveau le planning et essayez d&#39;ajouter une **Date de fin**. Une erreur se produira.
1. Actualisez la page et accédez à nouveau à **Modifier la mise à jour planifiée**.
1. Cliquez sur **Supprimer de la mise à jour** > **Supprimer la mise à jour**.
1. Maintenant, la mise à jour planifiée ne doit pas s’afficher en haut de la page de modification du produit.
1. Essayez de créer une nouvelle mise à jour planifiée qui chevauche la durée précédente.

<u>Résultats attendus</u> :

* Il n’y a aucune erreur à l’étape 4. L’administrateur peut mettre à jour la mise à jour planifiée sans erreur car le planning n’est pas encore actif.
* L’utilisateur administrateur peut supprimer la mise à jour précédente et en créer une nouvelle.

<u>Résultats réels</u> :

Les utilisateurs reçoivent le message d’erreur suivant :

*error : Future Update existe déjà dans cette période. Définissez une autre plage et réessayez.*


## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
