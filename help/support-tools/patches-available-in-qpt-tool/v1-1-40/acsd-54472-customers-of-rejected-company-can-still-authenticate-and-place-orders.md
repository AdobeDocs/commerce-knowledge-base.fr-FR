---
title: 'ACSD-54472 : les clients d’une société refusée peuvent toujours s’authentifier'
description: Appliquez le correctif ACSD-54472 pour résoudre le problème Adobe Commerce en raison duquel les clients d’une société rejetée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472 : les clients d’une société refusée peuvent toujours s’authentifier.

Le correctif ACSD-54472 corrige le problème en raison duquel les clients d’une société rejetée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.40 est installée. L’ID de correctif est ACSD-54472. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients d’une société refusée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes.

<u>Étapes à reproduire</u>:

1. Créez une société.
1. Ajoutez des produits au panier via [!DNL GraphQL].
1. Remplacez le statut de la société par *Bloqué*.
1. Envoyer un [!DNL GraphQL] demande de placer la commande et de créer un guillemet négociable.
1. Remplacez le statut de la société par *Rejetés*.
1. Envoyer un [!DNL GraphQL] demande d’obtention du jeton d’autorisation utilisateur de l’entreprise.
1. Définissez le statut du client sur *Inactif*.
1. Envoyer un [!DNL GraphQL] demande d’obtention du jeton d’autorisation utilisateur de l’entreprise.

<u>Résultats attendus</u>:

* L’utilisateur de la fonction *Bloqué* société.
* Le jeton d’autorisation n’est pas obtenu pour l’utilisateur de la fonction *Rejetés* société.
* Le jeton d’autorisation n’est pas obtenu pour la variable *Inactif* client.

<u>Résultats réels</u>:

* L’utilisateur de la fonction *Bloqué* société.
* Le jeton d’autorisation est obtenu pour l’utilisateur de la fonction *Rejetés* société.
* Le jeton d’autorisation est obtenu pour la variable *Inactif* client.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
