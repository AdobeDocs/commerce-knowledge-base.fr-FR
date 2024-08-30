---
title: 'ACSD-60441 : la mise à jour des clients via V1/customers [!DNL REST] Le point d’entrée API renvoie une erreur'
description: Appliquez le correctif ACSD-60441 pour résoudre le problème Adobe Commerce en raison duquel la mise à jour des clients via l’API V1/customers [!DNL REST] lors de l’utilisation d’un jeton d’accès à l’intégration généré à partir du serveur principal renvoie une erreur.
feature: REST, Customers
role: Admin, Developer
source-git-commit: ea62d2387ab0c04fe44291df431f42d78a0d2f2a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-60441 : la mise à jour des clients via le point d’entrée de l’API `V1/customers` [!DNL REST] renvoie une erreur

Le correctif ACSD-60441 corrige le problème en raison duquel la mise à jour des clients via l’API `V1/customers` [!DNL REST] lors de l’utilisation du jeton d’accès d’intégration généré à partir du serveur principal entraîne une erreur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-60441. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions Adobe Commerce**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour des clients via le point d’entrée de l’API `V1/customers` [!DNL REST] lors de l’utilisation du jeton d’accès à l’intégration généré à partir du serveur principal renvoie une erreur.

<u>Étapes à reproduire</u> :

1. Créez une intégration à partir de l’administrateur.
1. Envoyez une requête [!DNL POST] à `rest/default/V1/customers/<customer_id>` à l’aide du jeton d’intégration.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Résultats attendus</u> :

Les données client sont mises à jour.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante :

    &quot;json
    {
    &quot;message&quot; : &quot;Un client avec la même adresse électronique existe déjà dans un site Web associé.&quot;,
    &quot;trace&quot;: ...
    
    &quot;

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
