---
title: "ACSD-49480 : Ignorer les règles suivantes qui ne fonctionnent pas"
description: Appliquez le correctif ACSD-49480 pour résoudre le problème Adobe Commerce où [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480 : [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu

Le correctif ACSD-49480 corrige le problème lorsque [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.32 est installé. L’ID de correctif est ACSD-49480. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu.

<u>Étapes à reproduire</u> :

1. Créez un **[!UICONTROL Cart Price Rule]** avec un code de bon (nommez-le *TEST*) qui offre une remise de 10 $ à l’ *ID de produit 1* dans l’onglet **[!UICONTROL Actions]** avec [!UICONTROL Discard Subsequent Rules] défini sur *[!UICONTROL Yes]* et [!UICONTROL Priority] défini sur *1*.
1. Créez un autre **[!UICONTROL Cart Price Rule]** sans code de bon qui offre une remise de 5 $ à *ID de produit 2* dans l’onglet **[!UICONTROL Actions]** avec [!UICONTROL Priority] défini sur *2*. Ici, nous supposons qu’il s’agit d’une vente globale pour *ID de produit 2*.
1. Accédez au site front-end et ajoutez *ID de produit 1* et *ID de produit 2* dans le panier.
1. Appliquez le code de coupon *TEST*.

<u>Résultats attendus</u>

* *La remise 1* est appliquée à *l’ID de produit 1*.
* *La remise 2* est appliquée à *ID de produit 2*.

<u>Résultats réels</u>

* Seul *Discount 1* est appliqué à *ID de produit 1*.
* *Discount 2* n’est pas appliqué à *ID de produit 2*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
