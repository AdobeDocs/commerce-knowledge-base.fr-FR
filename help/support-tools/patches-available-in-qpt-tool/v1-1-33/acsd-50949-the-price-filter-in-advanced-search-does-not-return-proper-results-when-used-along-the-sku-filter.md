---
title: 'ACSD-50949 : le filtre de prix dans la recherche avancée ne renvoie pas de résultats corrects lorsqu’il est utilisé avec le filtre SKU'
description: Appliquez le correctif ACSD-50949 pour résoudre le problème Adobe Commerce en raison duquel le filtre de prix dans la recherche avancée ne renvoie pas de résultats appropriés lorsqu’il est utilisé avec le filtre SKU.
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949 : Le filtre de prix dans la recherche avancée ne renvoie pas de résultats corrects lorsqu’il est utilisé avec le filtre SKU.

Le correctif ACSD-50949 corrige le problème en raison duquel le filtre de prix dans la recherche avancée ne renvoyait pas de résultats appropriés lorsqu’il était utilisé avec le filtre SKU. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.33 est installée. L’ID de correctif est ACSD-50949. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Problème

Le filtre de prix dans la recherche avancée ne renvoie pas les résultats appropriés lorsqu’il est utilisé avec le filtre SKU.

<u>Étapes à reproduire</u>:

1. Créez plusieurs produits, par exemple :

   | SKU | Nom | Prix | Quantité |
   |-----|-----------|-------|----------|
   | MJ1 | Produit 1 | 10 $ | 10 |
   | MJ2 | Product 2 | 15 $ | 10 |
   | MJ3 | Product 3 | 21 $ | 10 |
   | MJ4 | Product 4 | 32 $ | 10 |
   | MJ5 | Product 5 | 33 $ | 10 |
   | MJ6 | Product 6 | 34 $ | 10 |
   | MJ7 | Product 7 | 44 $ | 10 |

1. Ouvrez le **[!UICONTROL Advanced Search]** sur Storefront et effectuez une recherche par SKU : &quot;MJ&quot;.
1. Cliquez sur le bouton **[!UICONTROL Modify your search]** lien.
1. Ajoutez une plage de prix au critère à partir de *1* to *21*, puis cliquez sur le bouton **[!UICONTROL Search]** bouton .

<u>Résultats attendus</u>:

Seuls les produits dont les prix sont compris dans la plage définie sont renvoyés.

<u>Résultats réels</u>:

Produits dont les prix sont supérieurs à *21 $* sont renvoyées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
