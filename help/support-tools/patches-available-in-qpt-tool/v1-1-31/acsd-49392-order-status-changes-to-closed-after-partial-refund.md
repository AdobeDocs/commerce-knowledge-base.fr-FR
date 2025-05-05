---
title: "ACSD-49392 : la commande passe en état de fermeture après remboursement partiel"
description: Appliquez le correctif ACSD-49392 pour résoudre le problème Adobe Commerce en raison duquel l’état de la commande se ferme après un remboursement partiel d’un produit regroupé.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392 : le statut de la commande passe à fermé après remboursement partiel

Le correctif ACSD-49392 corrige le problème en raison duquel l’état de la commande se ferme après un remboursement partiel pour un produit groupé. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.31 est installé. L’ID de correctif est ACSD-49392. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.3.7-p4 et 2.4.1 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut de la commande passe à Fermé après un remboursement partiel pour un produit fourni.

<u>Étapes à reproduire</u> :

1. Connectez-vous à Adobe Commerce et créez un produit regroupé ou utilisez le produit déjà regroupé.
1. passer une commande avec ce produit groupé dont la quantité est supérieure à 1 ;
1. Accédez à admin, ouvrez la commande créée à l’étape 2 à partir de **[!UICONTROL Sales]** > **[!UICONTROL Order]** et créez une facture. Observez l’état de la commande. Il sera en traitement.
1. Créez un avoir partiel (ne remboursez pas tous les produits du lot).
1. Vérifiez l’état de la commande.

<u>Résultats attendus</u>

Après la création d’une note de crédit partielle pour le produit regroupé, l’état de la commande est en cours de traitement.

<u>Résultats réels</u>

Après la création d’une note de crédit partielle pour le produit regroupé, l’état de la commande est terminé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
