---
title: "ACSD-51471 : l’utilisateur administrateur ne peut pas enregistrer la mise à jour planifiée pour le produit groupé"
description: Appliquez le correctif ACSD-51471 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur ne peut pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple avec une mise à jour planifiée.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471 : L’utilisateur administrateur ne peut pas enregistrer la mise à jour planifiée pour le produit groupé.

Le correctif ACSD-51471 corrige le problème lorsqu’un utilisateur administrateur ne peut pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple avec une mise à jour planifiée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 est installé. L’ID de correctif est ACSD-51471. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple dont la mise à jour est planifiée.

<u>Étapes à reproduire</u> :

1. Créez un produit simple.
1. Ajoutez une mise à jour planifiée pour le produit simple avec uniquement la *Date de début* et aucune *Date de fin*.
1. Une fois la mise à jour appliquée, modifiez le SKU du produit.
1. Créez un produit groupé et ajoutez le produit simple créé à l’étape 1 en tant que produit enfant.
1. Créez une mise à jour planifiée pour le produit regroupé afin d’activer ce dernier. Indiquez *Date de début* et *Date de fin* pour la mise à jour planifiée.
1. Enregistrez la mise à jour planifiée.

<u>Résultats attendus</u> :

La mise à jour planifiée a bien été enregistrée.

<u>Résultats réels</u> :

L&#39;erreur suivante se produit lors de l&#39;enregistrement de la mise à jour planifiée : *Le produit demandé n&#39;existe pas. Vérifiez le produit et réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
