---
title: "ACSD-51845 : impossible de mettre à jour les produits suivants avec les prix de niveau et différents ensembles d’attributs via asynch bulk - [!DNL API]"
description: Appliquez le correctif ACSD-51845 pour résoudre le problème d’Adobe Commerce en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et des ensembles d’attributs différents via asynchrones en masse. [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845 : impossible de mettre à jour les produits suivants avec des prix de niveau et des ensembles d’attributs différents via asynch global [!DNL API]

Le correctif ACSD-51845 corrige le problème en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et des ensembles d’attributs différents via asynchrones en masse. [!DNL REST API]. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-51845. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour échoue pour les produits suivants avec des prix de niveau et différents ensembles d’attributs via le mode asynchrone [!DNL REST API].

<u>Étapes à reproduire</u>:

1. Configurer [!DNL RabbitMQ].
1. Créez deux jeux d’attributs.
1. Créer deux **Produits simples**, attribuant chaque produit à un jeu d’attributs différent.
1. Ajouter un **Prix du groupe de clients** pour chaque produit.
1. Mettre à jour les deux produits en même bloc [!DNL API] mettre à jour.
1. Assurez-vous que la variable `bin/magento queue:consumers:start async.operations.all` est en cours d’exécution.
1. Vérifier le bloc [!DNL API] statut.

<u>Résultats attendus</u>:

L’exécution du service a réussi.

<u>Résultats réels</u>:

Le système renvoie le message d’erreur suivant : *Le produit n’a pas pu être enregistré. Veuillez réessayer.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
