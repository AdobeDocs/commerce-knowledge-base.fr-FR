---
title: 'ACSD-51666 : Erreur "La session a expiré, veuillez vous reconnecter." après vous être connecté'
description: Appliquez le correctif ACSD-51666 pour résoudre le problème Adobe Commerce où l’erreur *La session a expiré, veuillez vous reconnecter.* survient une fois que vous avez essayé de vous connecter.
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666 : Erreur *La session a expiré, veuillez vous reconnecter.* après vous être connecté

Le correctif ACSD-51666 corrige le problème où l’erreur *La session a expiré, veuillez vous reconnecter.* se produit une fois que vous avez essayé de vous connecter. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 est installé. L’ID de correctif est ACSD-51666. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous obtenez l’erreur *La session a expiré, veuillez vous reconnecter.* lors de la tentative de connexion avec le nouveau mot de passe d’un appareil après la réinitialisation du mot de passe sur un autre appareil. Cela se produit uniquement s’il existe une requête Ajax supplémentaire sur la page ajoutée par un module personnalisé.

<u>Étapes à reproduire</u> :

1. Installez un module personnalisé qui ajoute une requête Ajax sur chaque page du storefront.
1. Créez un compte.
1. Déconnectez-vous et revenez à la page de connexion.
1. Ouvrez le lien *Mot de passe oublié* dans un autre navigateur et envoyez l’e-mail *Réinitialiser le mot de passe*.
1. Ouvrez l’e-mail de réinitialisation de mot de passe dans le premier navigateur et définissez le nouveau mot de passe.
1. Essayez de vous connecter dans le deuxième navigateur.

<u>Résultats attendus</u> :

Vous pouvez vous connecter correctement lors de la première tentative.

<u>Résultats réels</u> :

* Vous voyez que la session *a expiré, veuillez vous reconnecter.* erreur.
* Vous n’êtes pas connecté et redirigé vers la page d’accueil.
* Votre deuxième tentative de connexion a réussi.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
