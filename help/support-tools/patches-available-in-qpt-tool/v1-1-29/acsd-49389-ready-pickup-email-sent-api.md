---
title: "ACSD-49389 : Prêt pour l’e-mail de récupération envoyé par l’API lorsqu’il n’est pas prêt pour la récupération"
description: Appliquez le correctif ACSD-49389 pour résoudre le problème Adobe Commerce en raison duquel un email prêt à être récupéré est envoyé par l’API lorsque la commande n’est pas prête pour la récupération.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389 : Prêt pour l’envoi d’un email de récupération par l’API lorsqu’il n’est pas prêt pour la récupération

Le correctif ACSD-49389 corrige le problème en raison duquel un email prêt à l’emploi est envoyé par l’API lorsque la commande n’est pas prête pour la récupération. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.29 est installée. L’ID de correctif est ACSD-49389. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [Page d’entrée QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message électronique prêt à l’emploi est envoyé par l’API lorsque la commande n’est pas prête pour la récupération.

<u>Étapes à reproduire</u>:

1. Activer *[!UICONTROL In-Store Delivery]* .
1. Créez une source de stock dont l’emplacement de récupération est activé.
1. Créez un nouveau stock à l&#39;aide du site web principal avec la source créée ci-dessus.
1. Créez un produit affectant la même source.
1. Définissez la quantité de stock = 1.
1. Extrayez le produit créé à l’étape 4 à l’aide du *[!UICONTROL In-Store Delivery]* du storefront.
1. Créez une facture pour la commande.
1. Définissez la quantité du produit sur *0* et le faire à partir du stock.
1. Publiez la requête API suivante :

```
{
    "orderIds": [
        1
    ]
}
```

<u>Résultats attendus</u>:

Les emails prêts pour la récupération ne sont pas envoyés.

<u>Résultats réels</u>:

Renvoie les API *La commande n’est pas prête pour la récupération*, mais un email prêt à être récupéré est envoyé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
