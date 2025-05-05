---
title: "ACSD-51845 : impossible de mettre à jour les produits suivants avec les prix de niveau et différents ensembles d’attributs via asynch bulk  [!DNL API]"
description: Appliquez le correctif ACSD-51845 pour résoudre le problème d’Adobe Commerce en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et des jeux d’attributs différents via asynchrones bulk  [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845 : impossible de mettre à jour les produits suivants avec des prix de niveau et des ensembles d&#39;attributs différents via asynch bulk [!DNL API]

Le correctif ACSD-51845 corrige le problème en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et des ensembles d’attributs différents via le lot asynchrone [!DNL REST API]. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-51845. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour échoue pour les produits suivants avec des prix de niveau et différents ensembles d’attributs via asynchrones en masse [!DNL REST API].

<u>Étapes à reproduire</u> :

1. Configurez [!DNL RabbitMQ].
1. Créez deux jeux d’attributs.
1. Créez deux **produits simples**, en attribuant chaque produit à un jeu d’attributs différent.
1. Ajoutez un **prix du groupe client** pour chaque produit.
1. Mettez à jour les deux produits dans la même mise à jour [!DNL API] en bloc.
1. Assurez-vous que la commande `bin/magento queue:consumers:start async.operations.all` est en cours d’exécution.
1. Vérifiez l’état [!DNL API] en masse.

<u>Résultats attendus</u> :

L’exécution du service a réussi.

<u>Résultats réels</u> :

Le système renvoie le message d&#39;erreur : *Le produit n&#39;a pas pu être enregistré. Réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
