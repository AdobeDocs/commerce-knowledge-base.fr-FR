---
title: Erreur lors de la validation des informations  [!DNL Fastly] ’identification
description: Cet article fournit une solution au problème d’erreur d’un utilisateur lors de la validation des informations  [!DNL Fastly] ’identification.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# Erreur lors de la validation des informations d’identification du [!DNL Fastly]

Cet article explique comment résoudre les erreurs *Jeton expiré* rencontrées lors de la validation des informations d’identification [!DNL Fastly].

Les étapes décrites dans cet article s’appliquent également si vous devez faire pivoter (redémarrer) votre jeton API [!DNL Fastly] pour des raisons de sécurité. Dans ce cas, vous devez envoyer un ticket d’assistance Adobe Commerce pour demander un nouveau jeton API [!DNL Fastly].

## Problème

* Une erreur s’affiche lors de la validation des informations d’identification du [!DNL Fastly].
* Vous pensez que votre jeton [!DNL Fastly] a pu être compromis, par exemple s’il a été partagé par inadvertance dans un ticket d’assistance ou publié sur un forum public.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) : toutes les versions
* [!DNL Fastly] de version de l’extension ou de la technologie ([!DNL New Relic], [!DNL Fastly], etc.)

## Solution

1. Vérifiez que vous disposez de l’identifiant de service [!DNL Fastly] et du jeton API corrects, puis réessayez de valider. Pour obtenir des instructions détaillées, reportez-vous à la section [Tester les informations  [!DNL Fastly] ’identification](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) de la documentation destinée aux développeurs.
1. Si la vérification des informations d’identification échoue, exécutez la commande curl suivante pour confirmer le statut du service :

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Si la commande ci-dessus renvoie une erreur similaire à : `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`, envoyez un ticket d’assistance pour demander un nouveau jeton API. Après avoir reçu votre nouveau jeton, mettez à jour la configuration dans votre environnement.

   Pour savoir comment envoyer un ticket d’assistance, reportez-vous au [Guide de l’utilisateur du centre d’aide Adobe Commerce > TICKETS D’ASSISTANCE](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-tickets) dans notre base de connaissances de l’assistance.

   >[!NOTE]
   >
   >Ne partagez jamais de mots de passe ou de jetons API valides/actifs directement dans le ticket, car nous devrons révoquer le jeton actuel et en générer un nouveau pour des raisons de sécurité.
   >
   >L’assistance Adobe Commerce a accès aux jetons. Vous n’avez donc pas besoin d’inclure ces informations dans le ticket.

1. Si la commande ne renvoie pas l’erreur, assurez-vous que vous exécutez la version la plus récente de l’extension [!DNL Fastly]. Si vous utilisez une version antérieure à la version 1.2.203, vous devez d’abord cliquer sur **[!UICONTROL Save Config]** avant de pouvoir tester les informations d’identification.

## Informations connexes dans notre documentation destinée aux développeurs :

* [Compte et informations d’identification Cloud for Adobe Commerce > [!DNL Fastly] > [!DNL Fastly] service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Cloud for Adobe Commerce > Configurer [!DNL Fastly] > Tester les informations  [!DNL Fastly] ’identification](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
