---
title: "ACSD-51230 : le compte de carte cadeau est supprimé"
description: Appliquez le correctif ACSD-51230 pour résoudre le problème Adobe Commerce en raison duquel le compte de carte-cadeau est supprimé lorsque le remboursement partiel d’un produit simple est traité à partir d’une commande.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230 : le compte de carte cadeau est supprimé

Le correctif ACSD-51230 corrige le problème de suppression du compte de carte-cadeau lorsque le remboursement partiel d’un produit simple est traité à partir d’une commande. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.32 est installée. L’ID de correctif est ACSD-51230. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le compte de carte-cadeau est supprimé lorsque le remboursement partiel d’un produit simple est traité à partir d’une commande.

<u>Étapes à reproduire</u>:

1. Créez une commande avec un *Carte cadeau* et un *produit simple* (par exemple, *add : SKU : GI000XX00XXX, SKU : PC046CP042076*) - (tout mode de paiement et de livraison fonctionne).
1. Facturez la commande.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Un compte est créé pour la carte-cadeau.
1. Accédez à **[!UICONTROL Order]**, puis créez un **[!UICONTROL Credit Memo]**.
1. Modifiez la quantité de la variable *Carte cadeau* sur 0 et mettez-le à jour. Cela créera un remboursement partiel de la valeur *produit simple*.
1. Cliquez sur **[!UICONTROL Refund]**.
1. Actualisez maintenant le **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Le compte nouvellement créé est supprimé.

<u>Résultats attendus</u>

Le compte de carte-cadeau peut être utilisé, car le remboursement n’a pas été créé pour la carte-cadeau.

<u>Résultats réels</u>

Le compte de carte-cadeau est supprimé et la carte-cadeau n’est pas remboursée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
