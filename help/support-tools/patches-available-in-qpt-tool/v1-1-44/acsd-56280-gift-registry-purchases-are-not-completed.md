---
title: "ACSD-56280 : les achats du registre des cadeaux ne sont pas terminés"
description: Appliquez le correctif ACSD-56280 pour résoudre le problème Adobe Commerce où les achats du registre des cadeaux ne sont pas terminés.
feature: Checkout
role: Admin
exl-id: 8e78ea1d-bd55-49d7-9d74-748b8f90e28c
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56280 : les achats du registre des cadeaux ne sont pas terminés

Le correctif ACSD-56280 corrige le problème lorsque les achats du registre des cadeaux ne sont pas terminés. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.44 est installée. L’ID de correctif est ACSD-56280. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les achats effectués dans le registre des cadeaux ne sont pas terminés.

<u>Étapes à reproduire</u>:

1. Connectez-vous en tant que client et ajoutez une **[!UICONTROL product]** au registre des cadeaux.
1. Partagez le lien du registre des cadeaux.
1. Ouvrez le lien du registre des cadeaux dans une autre fenêtre de navigateur/incognito.
1. Ajoutez la quantité et ajoutez les éléments au panier.
1. Accédez au **[!UICONTROL Checkout Page]**, sélectionnez **[!UICONTROL shipping method]**(Comme l’adresse de livraison est déjà sélectionnée, fournie par le déclarant).
1. Sélectionnez le mode de paiement.
1. Cliquez sur le bouton Passer commande .

<u>Résultats attendus</u>:

La commande doit être passée.

<u>Résultats réels</u>:

La commande n&#39;est pas placée et l&#39;erreur affichée est : `Call to a member function getUpdatedQty() on null`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
