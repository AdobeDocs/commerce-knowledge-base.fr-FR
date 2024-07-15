---
title: Dépannage de PayPal sur Adobe Commerce
description: Cet article fournit des solutions aux problèmes de traitement des paiements via PayPal, en particulier la solution PayFlow Pro. Certaines recommandations de cet article peuvent sembler évidentes. Nous vous demandons de tester les options de dépannage répertoriées dans cette base de connaissances et d’inclure toutes les informations dans les tickets que vous saisissez. Les ingénieurs du support Adobe Commerce ou PayPal vous demanderont d’effectuer ces étapes lors du diagnostic de vos problèmes.
exl-id: f0772515-8456-4f08-84b4-aeef44516f2a
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Dépannage de PayPal sur Adobe Commerce

Cet article fournit des solutions aux problèmes de traitement des paiements via PayPal, en particulier la solution PayFlow Pro. Certaines recommandations de cet article peuvent sembler évidentes. Nous vous demandons de tester les options de dépannage répertoriées dans cette base de connaissances et d’inclure toutes les informations dans les tickets que vous saisissez. Les ingénieurs du support Adobe Commerce ou PayPal vous demanderont d’effectuer ces étapes lors du diagnostic de vos problèmes.

## Problèmes courants

La plupart des problèmes liés aux paiements PayPal présentent des symptômes similaires : après avoir spécifié les détails de la carte de paiement et après avoir passé en caisse, le paiement n’est pas en cours de traitement. Au lieu de cela, il peut y avoir un message d’erreur, un échec de traitement du paiement ou même une page vierge.

## Vérification des informations d’identification, du chiffrement des clés et des licences

Problèmes possibles : erreurs d’impression dans les détails du compte (noms d’utilisateur, mots de passe), comptes non valides, licences expirées ou non spécifiées, clés publiques et personnelles non valides, etc. Pour résoudre ces problèmes, vous devrez peut-être également vérifier les paramètres de configuration des paiements.

## Application de paramètres cohérents dans Adobe Commerce et PayPal

Assurez-vous d’avoir appliqué les mêmes paramètres et d’avoir activé les mêmes fonctionnalités dans les paramètres du compte administrateur Commerce et du compte PayPal.

### Problème de paramètres d’exemple

Lors de l’application de la solution PayPal Express Checkout, les transactions basées sur les réponses AVS/CSC doivent être refusées dans **PayPal Manager** (Paramètres du service > Configurer > Options de sécurité) et dans **Commerce Admin** ( **Magasins** > Configuration > **Ventes** > **Méthodes de paiement** ....)
![magento_paypal_settings_2.4.1.png](assets/magento_paypal_settings_2.4.1.png)
Pour plus d’informations, consultez la documentation : [PayPal](https://www.paypalobjects.com/en_US/vhelp/paypalmanager_help/setup.htm) et [Adobe Commerce](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html) dans notre guide d’utilisation.

## Autoriser les transactions de référence

Si votre mode de paiement PayPal implique une API avec des accords de facturation et des transactions de référence, assurez-vous qu’ils sont activés et configurés correctement dans vos paramètres.

### Résolution des problèmes supplémentaires

Reportez-vous aux articles suivants :

* [ La passerelle PayPal a rejeté la demande - problème de facture en double ](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) dans notre base de connaissances d&#39;assistance.
* [Modifiez l’ID d’incrément de la nouvelle entité de magasin](/help/how-to/general/change-increment-id-for-a-db-entity-order-invoice-credit-memo-etc-on-particular-store.md) dans notre base de connaissances de prise en charge.

## Contacter l’assistance technique pour collecter les logs de paiement avancés

Pour résoudre des problèmes de paiement complexes, l’équipe d’assistance d’Adobe Commerce peut vous demander d’appliquer un correctif dédié afin d’activer la journalisation avancée des paiements. Dans ce cas, vos étapes doivent être les suivantes :

[Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) avec les détails suivants :

* Indiquez votre problème avec autant de détails que possible.
* Liste des étapes que vous avez entreprises à partir de cet article, de la base de connaissances et d’autres ressources. Inclure tous les résultats.
* Demandez un correctif de journalisation avancée des paiements (numéro de référence MDVA-4352) et des instructions pour appliquer le correctif.

Si vous recevez le correctif de journalisation de paiement avancée :

* Appliquez le correctif.
* Collectez les journaux et joignez-les à votre [ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
* Attendez les recommandations supplémentaires de l’équipe d’assistance d’Adobe Commerce.
