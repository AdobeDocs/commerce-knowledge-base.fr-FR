---
title: "ACSD-52815 : le champ d’entrée pour le champ de quantité d’une source autre que la source par défaut ne prend en charge que 6 chiffres au maximum"
description: Appliquez le correctif ACSD-52815 pour résoudre le problème de performances d’Adobe Commerce en raison duquel le champ d’entrée pour le champ de quantité d’une source autre que la source par défaut ne prend en charge que 6 chiffres, à la différence de 8 pour un stock par défaut.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815 : le champ d’entrée pour le champ de quantité d’une source autre que la source par défaut ne prend en charge que 6 chiffres au maximum.

Le correctif ACSD-52815 corrige le problème en raison duquel le champ d’entrée pour le champ de quantité d’une source autre que la source par défaut ne prend en charge que 6 chiffres au maximum, à la différence de 8 pour un stock par défaut. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-52815. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le champ d’entrée pour le champ de quantité d’une source autre que la source par défaut ne prend en charge que 6 chiffres au maximum, contrairement à 8 pour un stock par défaut.

<u>Étapes à reproduire</u> :

1. Créez un nouveau stock et une nouvelle source.
1. Créez un produit dont le nouveau stock source est défini sur 123.
1. Vérifiez la quantité vendable (123).
1. Mettez à jour la quantité source vers 12345678.
1. Rechecez la quantité salable.

<u>Résultats attendus</u> :

La quantité vendable indique la quantité correcte.

<u>Résultats réels</u> :

La quantité vendable est 999999.9999.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
