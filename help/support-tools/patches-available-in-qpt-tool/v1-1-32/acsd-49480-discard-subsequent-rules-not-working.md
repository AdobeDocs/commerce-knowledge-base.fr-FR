---
title: "ACSD-49480 : Ignorer les règles suivantes qui ne fonctionnent pas"
description: Appliquez le correctif ACSD-49480 pour résoudre le problème Adobe Commerce où la variable [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480 : [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu

Le correctif ACSD-49480 corrige le problème en raison duquel la variable [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.32 est installée. L’ID de correctif est ACSD-49480. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu.

<u>Étapes à reproduire</u>:

1. Créez un **[!UICONTROL Cart Price Rule]** avec un code de bon (nommez-le comme *TEST*) qui offre une remise de 10 $ au *ID de produit 1* dans le **[!UICONTROL Actions]** avec [!UICONTROL Discard Subsequent Rules] défini sur *[!UICONTROL Yes]* et [!UICONTROL Priority] défini sur *1*.
1. Créer un autre **[!UICONTROL Cart Price Rule]** sans code de coupon qui offre une remise de 5 € à *ID de produit 2* dans le **[!UICONTROL Actions]** avec [!UICONTROL Priority] défini sur *2*. Ici, nous supposons que c&#39;est une vente mondiale pour *ID de produit 2*.
1. Accédez au site front-end et ajoutez *ID de produit 1* et *ID de produit 2* dans le panier.
1. Appliquez la variable *TEST* code de coupon.

<u>Résultats attendus</u>

* *Remise 1* s’applique à *ID de produit 1*.
* *Réduction 2* s’applique à *ID de produit 2*.

<u>Résultats réels</u>

* Uniquement *Remise 1* s’applique à *ID de produit 1*.
* *Réduction 2* n’est pas appliqué à *ID de produit 2*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
