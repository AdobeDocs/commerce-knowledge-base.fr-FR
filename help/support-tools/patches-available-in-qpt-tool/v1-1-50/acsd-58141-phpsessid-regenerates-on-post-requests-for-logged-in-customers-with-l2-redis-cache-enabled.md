---
title: "ACSD-58141 : PHPSESSID se régénère sur les demandes de POST pour les clients connectés avec le cache de Redis L2 activé"
description: Appliquez le correctif ACSD-58141 pour résoudre le problème Adobe Commerce en raison duquel &grave;PHPSESSID&grave; se régénère sur les demandes de POST dans la zone Storefront pour un client connecté avec le cache L2 Redis activé et le client est mis à jour à partir de l’administrateur.
feature: Customers, Cache
role: Admin, Developer
source-git-commit: 488699c5d880baee2f7191d963368415f90c3340
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# ACSD-58141 : PHPSESSID se régénère sur les demandes [!DNL POST] pour les clients connectés si le cache de Redis L2 est activé.

Le correctif ACSD-58141 corrige le problème en raison duquel `PHPSESSID` se régénère sur les requêtes [!DNL POST] d’un client connecté si le cache des Redis L2 est activé et que le client est mis à jour à partir de l’administrateur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-58141. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec Adobe Commerce et les versions de Magento Open Source :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`PHPSESSID` se régénère sur les demandes [!DNL POST] pour un client connecté avec le cache L2 Redis activé.

<u>Conditions préalables</u>

L’environnement doit être configuré avec Redis comportant au moins 3 noeuds.

<u>Étapes à reproduire</u> :

1. Créez un produit simple.
1. Créez un client et connectez-vous à Storefront.
1. Vérifiez la valeur de `PHPSESSID`.
1. Envoyez quelques requêtes [!DNL POST] (par exemple, l’ajout d’un produit au panier) et vérifiez que `PHPSESSID` reste le même).
1. Connectez-vous au panneau **[!UICONTROL Admin]** et modifiez le deuxième nom du client.
1. Lorsque le deuxième nom est enregistré, modifiez-le et enregistrez-le à nouveau quelques fois.
1. Sur le storefront, envoyez une requête [!DNL POST]. `PHPSESSID` doit avoir été mis à jour.
1. Sur le storefront, envoyez une autre requête [!DNL POST] et vérifiez `PHPSESSID`.
1. Répétez l’étape précédente quelques fois.

<u>Résultats attendus</u>

`PHPSESSID` n’est régénéré qu’une seule fois après avoir modifié les données client.

<u>Résultats réels</u> :

`PHPSESSID` est régénéré chaque fois que les demandes [!DNL POST] sont envoyées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
