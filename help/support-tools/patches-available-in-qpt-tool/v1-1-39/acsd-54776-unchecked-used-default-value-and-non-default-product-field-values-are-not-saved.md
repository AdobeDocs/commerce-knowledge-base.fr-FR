---
title: '''ACSD-54776 : non coché [!UICONTROL Use Default Value] Les valeurs des champs de produit et autres que par défaut ne sont pas enregistrées pour le deuxième site web, magasin et vue de magasin."'
description: Appliquez le correctif ACSD-54776 pour résoudre le problème Adobe Commerce où la case non cochée [!UICONTROL Use Default Value] Les valeurs des champs de produit et autres que par défaut ne sont pas enregistrées pour le deuxième affichage de site web, de magasin et de magasin.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776 : non coché *[!UICONTROL Use Default Value]* et les valeurs de champs de produit autres que par défaut ne sont pas enregistrées.

>[!NOTE]
>
>Ce correctif remplace le [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) correctif publié dans QPT 1.1.35.

Le correctif ACSD-54776 corrige le problème en raison duquel la commande non cochée **[!UICONTROL Use Default Value]** Les valeurs des champs de produit et autres que par défaut ne sont pas enregistrées pour le deuxième affichage de site web, de magasin et de magasin. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.39 est installée. L’ID de correctif est ACSD-54776. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Non coché *[!UICONTROL Use Default Value]* Les valeurs des champs de produit et autres que par défaut ne sont pas enregistrées pour le deuxième affichage de site web, de magasin et de magasin.

<u>Étapes à reproduire</u>:

1. Accédez au serveur principal et accédez à **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** et créer un site web, un magasin et une vue de magasin.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, créez un produit simple et enregistrez-le, puis attribuez-le aux deux sites web à partir de la fonction **[!UICONTROL Product in Websites]**.
1. Remplacez la portée par la nouvelle vue de magasin de l’étape 2.
1. Accédez à **[!UICONTROL Search Engine Optimization]** et désélectionnez la variable **[!UICONTROL Use Default Value]** des cases à cocher pour [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], et [!UICONTROL Meta Description].
1. Nettoyez le texte des champs : *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* et *[!UICONTROL Meta Description]*, puis cliquez sur **[!UICONTROL Save]**.
1. Accédez à **[!UICONTROL Search Engine Optimization]** encore une fois.

<u>Résultats attendus</u>

Les valeurs des champs et des cases à cocher sont enregistrées.

<u>Résultats réels</u>

Les valeurs des champs et des cases à cocher ne sont pas enregistrées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
