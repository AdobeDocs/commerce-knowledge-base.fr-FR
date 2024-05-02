---
title: '''[!DNL ACSD-47280]: désactiver le catalogue partagé donne les mauvais résultats de recherche de produits.'
description: Appliquez la variable [!DNL ACSD-47280] correctif pour corriger l’affichage des résultats de recherche corrects lorsque la fonction de catalogue partagé est désactivée.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: la désactivation du catalogue partagé donne de mauvais résultats de recherche de produits.

La variable [!DNL ACSD-47280] patch corrige l’affichage des résultats de recherche corrects lors de la [!DNL shared catalog] est désactivée. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.22 est installée. La variable [!DNL patch ID] is [!DNL ACSD-47280]. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez la variable [!DNL patch ID] comme mot-clé de recherche pour localiser le correctif.

## Problème

Désactivation [!DNL shared catalog] donne des résultats de recherche de produits incorrects.

<u>Conditions préalables</u>:

* [!DNL B2B] modules installés

<u>Étapes à reproduire</u>:

1. Créez un second site web.
1. Affectez un produit au deuxième site web.
1. Vérifiez les produits sur la page **deuxième site web** using [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Activer **[!UICONTROL Shared Catalog]** par défaut [!DNL scope].
1. La variable [!DNL GraphQL] n’affiche plus aucun produit pour le deuxième site web, ce qui est le résultat correct.
1. Accédez au [!DNL scope] de deuxième site web et désactiver **[!UICONTROL Company]**.

<u>Résultats attendus</u>:

La variable [!DNL GraphQL] La demande doit toujours afficher les produits pour le deuxième site web.

<u>Résultats réels</u>:

La variable [!DNL GraphQL] n’affiche aucun produit pour le deuxième site web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
