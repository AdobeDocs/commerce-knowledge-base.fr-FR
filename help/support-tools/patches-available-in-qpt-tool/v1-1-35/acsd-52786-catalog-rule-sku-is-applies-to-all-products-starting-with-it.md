---
title: 'ACSD-52786 : règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU'
description: Appliquez le correctif ACSD-52786 pour résoudre le problème Adobe Commerce où la condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786 : la règle de catalogue &quot;*[!UICONTROL SKU is]*&quot; s’applique à tous les produits commençant par le SKU.

Le correctif ACSD-52786 corrige le problème où la condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-52786. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné.

<u>Étapes à reproduire</u> :

1. Créez deux produits, l’un avec le SKU &quot;24&quot; et l’autre avec le SKU &quot;24-MB01&quot;.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Appliquez la condition suivante :
   * *[!UICONTROL If **&#x200B; ALL &#x200B;** de ces conditions sont **&#x200B; TRUE &#x200B;**]*: *[!UICONTROL SKU is 24]*
1. Définissez un montant de remise dans les actions.
1. Cliquez sur **[!UICONTROL Save and Apply]**.
1. Videz le cache.
1. Allez sur la vitrine, et vérifiez le prix de 24-MB01.

<u>Résultats attendus</u> :

La règle de catalogue s’applique uniquement à un seul produit dont le SKU est égal à 24.

<u>Résultats réels</u> :

La condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
