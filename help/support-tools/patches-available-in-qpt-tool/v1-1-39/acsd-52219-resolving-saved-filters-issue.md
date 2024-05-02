---
title: "ACSD-52219 : résolution du problème de filtre des grilles d’administration lors du changement d’affichage des signets"
description: Appliquez le correctif ACSD-52219 pour résoudre le problème Adobe Commerce en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnent pas comme prévu lors du basculement fréquent entre les vues des signets.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219 : résolution du problème de filtre des grilles d’administration lors du changement de vue de signet

Le correctif ACSD-52219 corrige le problème en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnent pas comme prévu lors du basculement fréquent entre les vues de signet. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.39 est installée. L’ID de correctif est ACSD-52219. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque vous passez fréquemment d’une vue de signet à l’autre, les filtres enregistrés dans les grilles d’administration ne fonctionnent pas comme prévu.

<u>Étapes à reproduire</u>:

1. Accédez au [!DNL Sales Order] grille dans Admin.
1. Créez deux à trois filtres.
1. Vérifiez les paramètres de filtre en changeant de vue pour vous assurer qu’ils sont enregistrés avec précision.
1. Accédez à Filter1 ou Filter2.
1. Actualisez la page pour mettre à jour les données affichées.
1. Basculez vers une autre vue et notez que les filtres restent inchangés.
1. La vue par défaut affiche désormais les résultats filtrés, même si aucun filtre spécifique n’a été défini pour celle-ci.

<u>Résultats attendus</u>:

Les filtres ne sont pas interchangés et conservent leur état d’origine.

<u>Résultats réels</u>:

Lors de la modification d’une vue, les filtres sont mélangés et la vue correcte n’est pas enregistrée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
