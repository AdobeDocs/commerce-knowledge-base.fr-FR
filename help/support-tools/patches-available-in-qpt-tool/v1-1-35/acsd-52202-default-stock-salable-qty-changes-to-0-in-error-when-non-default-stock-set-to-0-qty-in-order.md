---
title: 'ACSD-52202 : La valeur par défaut de la valeur de la valeur de stock Salable passe à 0 en erreur lorsque le stock non par défaut est défini sur 0 quantité dans l’ordre'
description: Appliquez le correctif ACSD-52202 pour résoudre le problème Adobe Commerce en raison duquel une quantité vendable par défaut de stock passe à 0 en erreur lorsque le stock non par défaut est défini sur 0 quantité dans une commande.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202 : La quantité vendue par défaut du stock passe à 0 en erreur lorsque le stock non par défaut est défini sur 0 quantité dans une commande.

Le correctif ACSD-52202 corrige le problème en raison duquel une quantité vendable par défaut (qty) passe à 0 par erreur lorsqu’un stock non par défaut est défini sur 0 quantité dans une commande. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-52202. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité vendue par défaut du stock passe à 0 en erreur lorsque le stock non par défaut est défini sur 0 quantité dans une commande.

<u>Étapes à reproduire</u>:

1. Connectez-vous au [!DNL Admin].
1. Créer **site web2**.
1. Créer des **source2**.
1. Créer des **stock2**.
1. Attribuez le **source2** et **stock2** to **site web1** et la source et le stock par défaut sur le site web par défaut.
1. Créez un produit simple et affectez-lui **qty** = *10* pour la source par défaut et **qty** = *1* pour le **source2** source.
1. Passer une commande avec **qty** = *1* pour **site web2**.
1. Créez une facture et une expédition.
1. Vérifier le produit simple **quantité vendable**.

<u>Résultats attendus</u>:

La variable **quantité vendable** = *10* pour **source2**.

<u>Résultats réels</u>:

La variable **quantité vendable** = *0* pour les deux sources.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
