---
title: Compte sandbox PayPal non vérifié
description: Cet article explique pourquoi il se peut que votre compte sandbox PayPal pour les services de paiement ne soit pas vérifié, ce qui vous empêche de terminer l’intégration à l’environnement de test.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Compte sandbox PayPal non vérifié

Cet article explique pourquoi il se peut que votre compte sandbox PayPal pour les services de paiement ne soit pas vérifié, ce qui vous empêche de terminer l’intégration à l’environnement de test.

## Produits et versions concernés

* [Services de paiement](https://marketplace.magento.com/magento-payment-services.html) est désormais compatible avec les versions 2.4.0 à 2.4.4 d’Adobe Commerce.

## Problème

Notre [documentation d’intégration](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) vous demande de vous inscrire à un compte PayPal, de vous connecter au compte des développeurs PayPal, puis de créer un compte sandbox. Si vous choisissez de créer un compte lors de l’intégration dans la fenêtre contextuelle d’intégration de PayPal, PayPal ne pourra pas vérifier votre compte sandbox et vous ne pourrez pas terminer l’intégration.

<u>Étapes à reproduire</u>:

1. You [installation des services de paiement](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) et [configuration des services Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Vous accédez à **Services de paiement** dans l’ administrateur et [démarrage de l’intégration à un environnement de test](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. Dans la fenêtre contextuelle d’intégration PayPal qui s’affiche, vous créez un compte professionnel (au lieu de [connexion avec un compte sandbox PayPal créé précédemment](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) lors de l’intégration.
1. Vous avez réussi l’intégration à PayPal.
1. Une notification s’affiche dans l’administrateur pour vous informer que vos paiements sandbox sont en attente et que vous devez confirmer votre adresse électronique avec PayPal pour terminer l’intégration.

   Vous n’avez pas reçu de courrier électronique de confirmation car PayPal n’a pas pu vérifier votre adresse électronique.

## Cause

PayPal ne pourra pas vérifier votre compte sandbox et vous ne pourrez pas terminer l’intégration des environnements de test (ce qui signifie que vous ne pouvez pas accepter de paiements ni tester votre mode sandbox) si vous créez votre compte sandbox avant votre compte PayPal.

## Solution

1. Utilisation d’un compte sandbox créé dans [Développeur PayPal](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portail.
1. Cliquez sur [réinitialisation de sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) et redémarrez l’intégration de votre environnement de test.
1. [Contacter le support technique](mailto:payment-services-support@adobe.com) si vous ne pouvez pas résoudre les problèmes liés à votre compte afin de pouvoir reprendre l’intégration et accepter des paiements.
