---
title: Erreur lors de la validation des informations d’identification Fastly
description: Cet article fournit une solution au problème où un utilisateur obtient une erreur lors de la validation des informations d’identification Fastly.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 831a928dbe8fd6b37f3fe9ad5dc35ee80e11a578
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Erreur lors de la validation des informations d’identification Fastly

Cet article fournit une solution au problème où un utilisateur obtient une erreur lors de la validation des informations d’identification Fastly.

## Problème

L’utilisateur reçoit une erreur lors de la validation des informations d’identification Fastly.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) : toutes les versions
* Extension ou technologie (Fastly, New Relic, etc.) version Fastly

## Solution

1. Assurez-vous que vous disposez de l’ID de service et du jeton d’API corrects et essayez à nouveau de valider. Pour obtenir des instructions détaillées, reportez-vous à la section [Test des informations d’identification Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials) dans notre documentation destinée aux développeurs.
1. Si la vérification des informations d’identification échoue, exécutez la commande curl suivante pour confirmer l’état du service :

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Si la commande ci-dessus renvoie une erreur similaire à : *{&quot;msg&quot;:&quot;Token $TOKEN expiré à 2021-09-28T02:03:37Z&quot;}*, soumettez un ticket de support pour demander un nouveau jeton API.

   Pour savoir comment envoyer un ticket d’assistance, reportez-vous au [Guide de l’utilisateur du centre d’aide Adobe Commerce > TICKETS D’ASSISTANCE](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) dans notre base de connaissances d’assistance.

   >[!NOTE]
   >
   >Ne partagez jamais de mots de passe ou de jetons API valides/actifs directement dans le ticket, car nous devrons révoquer le jeton actuel et en générer un nouveau pour des raisons de sécurité.

1. Si la commande ne renvoie pas l’erreur, assurez-vous que vous exécutez la dernière version de l’extension [!DNL Fastly]. Si vous utilisez une ancienne version antérieure à la version 1.2.203, vous devez d’abord cliquer sur **[!UICONTROL Save Config]** avant de pouvoir tester les informations d’identification.

## Lectures connexes dans notre documentation destinée aux développeurs :

* [Cloud pour Adobe Commerce > Fastly > Compte de service et informations d’identification Fastly](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html#fastly-service-account-and-credentials)

* [Cloud pour Adobe Commerce > Configurer rapidement > Tester les informations d’identification rapides](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials)
