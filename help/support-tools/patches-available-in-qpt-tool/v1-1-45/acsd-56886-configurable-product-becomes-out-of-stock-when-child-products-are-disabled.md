---
title: "ACSD-56886 : le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés"
description: Appliquez le correctif ACSD-56886 pour résoudre le problème Adobe Commerce où le produit configurable devient en rupture de stock enfant lorsque les produits sont désactivés.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886 : Le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés.

Le correctif ACSD-56886 corrige le problème en raison duquel le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 est installé. L’ID de correctif est ACSD-56886. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant qu’administrateur.
1. Définissez tous les indexeurs en mode **[!UICONTROL Update By Schedule]**.
1. Créez le produit configurable suivant :

   * Nom = *TEST CONFIGURABLE 1*
   * Attribut = *color*
   * Valeurs = *red* et *black*
   * Prix du **produit enfant rouge** = *$100*;
   * Prix du produit enfant &quot;noir&quot; = *$200*.

1. Créez la mise à jour planifiée suivante pour le produit configurable :

   * Date de début = *3* minutes à partir de maintenant.
   * Date de fin = *5* minutes après la date de début.
   * Nom du produit = *TEST CONFIGURABLE 1 modifié*.
   * Désactivez le produit enfant **red** dans la section **Configurable** .

1. Attendez la date de début.
1. Ouvrez les détails du produit configurables sur Storefront.

<u>Résultats attendus</u> :

Le produit configurable s’affiche sous la forme **En stock** avec l’étiquette **Aussi basse que 200**.

<u>Résultats réels</u> :

Le produit configurable s’affiche sous la forme **En rupture de stock**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
