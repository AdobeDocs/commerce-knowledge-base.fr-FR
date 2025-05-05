---
title: "ACSD-51892 : problème de performances où les fichiers de configuration se chargent plusieurs fois"
description: Appliquez le correctif ACSD-51892 pour résoudre le problème de performances Adobe Commerce en raison duquel les fichiers de configuration se chargent plusieurs fois pendant le déploiement.
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892 : problème de performances où les fichiers de configuration se chargent plusieurs fois

Le correctif ACSD-51892 corrige le problème de performances qui survient lors du chargement des fichiers `app/etc/env.php` et `app/etc/config.php` chaque fois que les valeurs de configuration de déploiement sont accessibles dans une seule requête. La lecture excessive des fichiers met à rude épreuve le système, ce qui entraîne une détérioration des performances globales. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.33 est installé. L’ID de correctif est ACSD-51892. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6-p2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il existe un problème de performances où les fichiers de configuration se chargent plusieurs fois.

<u>Étapes à reproduire</u> :

1. Effectuez le déploiement ou la mise à niveau vers Adobe Commerce 2.4.6 ou version ultérieure.
1. Vérifiez les journaux du système de fichiers pour accéder aux fichiers `app/etc/env.php` et `app/etc/config.php` pendant l’exécution du déploiement.

<u>Résultats attendus</u> :

Le déploiement réussit dans le délai normal.

<u>Résultats réels</u> :

* Les serveurs ont du mal à répondre aux commandes que vous saisissez. Cela se traduit par l’ *erreur 503 first byte timeout* lors de l’accès au site web.
* Il existe plusieurs entrées dans les fichiers journaux ayant accès aux fichiers `app/etc/env.php` et `app/etc/config.php`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
