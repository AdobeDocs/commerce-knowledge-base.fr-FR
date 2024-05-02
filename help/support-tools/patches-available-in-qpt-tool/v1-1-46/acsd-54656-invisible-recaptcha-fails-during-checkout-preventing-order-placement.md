---
title: Invisible [!DNL reCAPTCHA] échoue lors de l’extraction, empêchant le placement de la commande
description: Appliquez le correctif ACSD-54656 pour résoudre le problème Adobe Commerce où l’invisible [!DNL reCAPTCHA] ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656 : Invisible [!DNL reCAPTCHA] ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande.

Le correctif ACSD-54656 corrige le problème où l’invisible [!DNL reCAPTCHA] ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.46 est installée. L’ID de correctif est ACSD-54656. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Invisible [!DNL reCAPTCHA] ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande.

<u>Étapes à reproduire</u>:

1. Activez tout type de [!DNL reCAPTCHA] pour une carte-cadeau sur le [!UICONTROL Checkout] page.
1. Ajoutez un produit au panier et accédez au **[!UICONTROL Checkout]** page.
1. Développez le formulaire de carte-cadeau et remplissez un bon de carte-cadeau valide.
1. Cliquez sur **[!UICONTROL See balance and apply]** bouton .

<u>Résultats attendus</u>:

La carte cadeau a été appliquée avec succès.

<u>Résultats réels</u>:

Le message d’erreur s’affiche : *[!DNL reCAPTCHA]échec de la validation, veuillez réessayer*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
