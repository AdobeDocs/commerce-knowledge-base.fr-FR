---
title: "ACSD-59514 : Forms dans l’administration avec  [!DNL Page Builder] générer une erreur dans la console du navigateur"
description: Appliquez le correctif ACSD-59514 pour résoudre le problème Adobe Commerce en raison duquel les formulaires dans Admin avec  [!DNL Page Builder]  renvoyaient l’erreur "[!DNL Page Builder]" pendant 5 secondes sans déclencher de verrous. dans la console du navigateur après l’envoi du formulaire, et les modifications ne peuvent pas être enregistrées.
feature: Page Builder
role: Admin, Developer
source-git-commit: 19ecaa6b287d63bfae00c51911b53e1ed7ab5ed8
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-59514 : Forms dans Admin avec [!DNL Page Builder] renvoie une erreur dans la console du navigateur.

Le correctif ACSD-59514 corrige le problème en raison duquel les formulaires dans l’administration avec [!DNL Page Builder] généraient l’erreur *[!DNL Page Builder]pendant 5 secondes sans déclencher de verrous.* dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 est installé. L’ID de correctif est ACSD-59514. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Forms dans Admin avec [!DNL Page Builder] renvoie l’erreur *[!DNL Page Builder]qui a été générée pendant 5 secondes sans déclencher de verrous.* dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées.

<u>Conditions préalables</u> :

Les modules Adobe Commerce [!DNL Page Builder] sont installés et activés.

<u>Étapes à reproduire</u> :

1. Ouvrez le panneau d’administration et cliquez sur le bouton [!UICONTROL Content] .
1. Sélectionnez le bloc et éditez-le.
1. Modifiez le contenu et cliquez sur [!UICONTROL Save].
1. Ouvrez la console et affichez le message d’erreur.

<u>Résultats attendus</u> :

Le bloc est enregistré avec succès.

<u>Résultats réels</u> :

Le chargeur n&#39;arrête pas de tourner et le bloc n&#39;est pas enregistré. L’erreur suivante s’affiche dans la console du navigateur :
*[!DNL Page Builder]a effectué un rendu pendant 5 secondes sans relâcher de verrous.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
