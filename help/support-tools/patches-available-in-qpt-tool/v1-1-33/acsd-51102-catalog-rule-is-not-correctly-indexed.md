---
title: "ACSD-51102 : règle de catalogue appliquée à un grand nombre de produits incorrectement indexés"
description: Appliquez le correctif ACSD-51102 pour résoudre le problème Adobe Commerce en raison duquel une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102 : règle de catalogue appliquée à un grand nombre de produits mal indexés

Le correctif ACSD-51102 corrige le problème lorsqu’une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.33 est installée. L’ID de correctif est ACSD-51102. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.

Conditions préalables :

* La tâche Cron est configurée et s’exécute toutes les minutes.

<u>Étapes à reproduire</u>:

1. Créez un catalogue volumineux contenant des milliers de produits afin d’obtenir le temps d’exécution de la variable *règle de catalogue* indexeurs de plus de 120 secondes lorsque les règles de catalogue sont activées.
2. Créez deux règles de catalogue avec *Actif* défini sur *Non*.  Par exemple : *Test 1* et *Test 2*. Chaque règle doit affecter tous les produits du catalogue et provoquer l’exécution de l’indexeur pendant plus de 120 secondes.
3. Assurez-vous que l’état de l’indexeur est *Prêt*.
4. Créez des mises à jour planifiées pour activer ces deux règles. *Test 2* le planning doit commencer peu après *Test 1*. Par exemple, avec une différence de 1 minute.
5. Vérifiez les prix des produits sur le storefront.

<u>Résultats attendus</u>

Les remises des deux règles sont appliquées.

<u>Résultats réels</u>

Seule la première remise de règle est appliquée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
