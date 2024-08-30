---
title: '"ACSD-45049 : le paramètre d’attribut "Le client est requis" ne fonctionne pas selon la portée du site web dans Admin"'
description: Appliquez le correctif ACSD-45049 pour résoudre le problème Adobe Commerce en raison duquel l’attribut "[!UICONTROL Is required]" du client n’est pas correctement remplacé conformément à la portée du site web dans Admin.
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: 16e7c9e4e4bbbc62db0671016bce85ecb6414622
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-45049 : le paramètre d’attribut *[!UICONTROL Is required]* du client ne fonctionne pas selon la portée du site web dans Admin

Le correctif ACSD-45049 corrige le problème en raison duquel le paramètre d’attribut customer *[!UICONTROL Is required]* ne fonctionne pas correctement selon la portée du site web dans Admin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.50 est installé. L’ID de correctif est ACSD-45049. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p7 et 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le paramètre d’attribut *[!UICONTROL Is required]* du client ne fonctionne pas correctement selon la portée du site web dans Admin.

<u>Étapes à reproduire</u> :

1. Créez deux sites web.
1. Ouvrez **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Créez un nouvel attribut, définissez **[!UICONTROL Is value required]** = *Non*.
1. Basculez vers le site web par défaut, puis modifiez **[!UICONTROL Is value required]** = *Oui*. L’autre site web possède la valeur par défaut.
1. Créez un client à partir de l’administrateur pour le site web autre que celui par défaut.

<u>Résultats attendus</u> :

L’attribut n’est pas obligatoire pour le site web autre que celui par défaut.

<u>Résultats réels</u> :

* L’attribut est requis pour le site web autre que le site par défaut lors de la création d’un client dans Admin.
* L’attribut n’est pas obligatoire pour le site web autre que celui par défaut lors de l’enregistrement d’un client sur le storefront.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
