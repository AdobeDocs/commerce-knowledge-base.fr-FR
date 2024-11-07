---
title: Activité de carte active PayPal Payflow Pro
description: MISE À JOUR 2 avril 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Activité de carte active PayPal Payflow Pro

MISE À JOUR 2 avril 2019

L’intégration de PayPal Payflow Pro dans Adobe Commerce est activement ciblée par l’activité de carte, où les attaquants tentent des centaines de transactions de 0 $ avec des cartes de crédit volées pour vérifier la validité de la carte.

L’activité cible actuellement les versions de cette intégration de Payflow Pro qui ont été incluses dans Adobe Commerce 2.1.x, 2.2.x, 2.3.x pour Magento Open Source et Commerce (sur site et dans le cloud). L’activité de carte est inhérente à la manière dont Payflow Pro est intégré aux paniers.

>[!NOTE]
>
>Pour vous aider à résoudre ces problèmes, nous avons fourni de nouveaux modules Compositeur afin d’ajouter Google reCAPTCHA ou CAPTCHA au formulaire de paiement de Payflow Pro. Nous vous recommandons d’installer ces packages sur toutes les versions et éditions d’Adobe Commerce.

Le problème affecte les versions d’Adobe Commerce suivantes :

* Adobe Commerce sur site v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce sur l’infrastructure cloud v2.1.x, 2.2.x, 2.3.x

## Problème

Les symptômes de ces attaques sont les suivants :

* Votre compte PayPal Payflow Pro affiche des centaines de transactions frauduleuses identifiées
* PayPal peut suspendre un compte Payflow Pro en raison de transactions de fraude entrantes et facturer des frais importants.

## Solution

Pour vous aider à vous protéger de ces attaques, nous vous conseillons d’ajouter Google reCAPTCHA (recommandé) ou CAPTCHA au formulaire de paiement de Payflow Pro. Cela inclut l’installation des packages du compositeur et la configuration de Google reCAPTCHA ou CAPTCHA dans l’administrateur Commerce.

### Installation de packages

Adobe a créé deux options de package pour ajouter Google reCAPTCHA et/ou CAPTCHA au formulaire de paiement de Payflow Pro. L’installation de l’un de ces packages met à jour les installations en cours et ajoute une option qui peut contribuer à améliorer cette sécurité dans le formulaire de passage en caisse de Payflow Pro.

Ces packages sont compatibles avec les versions et déploiements Adobe Commerce suivants :

Adobe Commerce (toutes les méthodes de déploiement) et Magento Open Source 2.1.x, 2.2.x, 2.3.x

L’installation requiert des commandes d’interface de ligne de commande pour votre instance Adobe Commerce. Une assistance aux développeurs peut être nécessaire.

>[!NOTE]
>
>Nous vous recommandons d’installer et de configurer Google reCAPTCHA en plus d’installer les mises à jour appropriées du formulaire de passage en caisse de Payflow Pro. Cette option fournit une vérification invisible et plusieurs options de configuration.

#### Installer Google reCAPTCHA et les mises à jour des formulaires de passage en caisse

Le package `magento/module-paypal-recaptcha` contient l’intégration avec les mises à jour des formulaires de paiement Google reCAPTCHA et Payflow Pro. Même si le module reCAPTCHA est installé et configuré, nous vous recommandons d’installer ce package.

Exécutez les commandes suivantes pour l’installer.

**Pour Adobe Commerce sur site :**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Pour Adobe Commerce sur l’infrastructure cloud :**

1. Exécutez la commande suivante :

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Validation et transmission des modifications :

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Attendez que le déploiement soit terminé.

#### Installer les mises à jour des formulaires de passage en caisse pour CAPTCHA

Le package `magento/module-paypal-captcha` contient l’intégration au module Adobe Commerce CAPTCHA natif.

Exécutez les commandes suivantes pour l’installer :

**Pour Adobe Commerce sur site :**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Pour Adobe Commerce sur l’infrastructure cloud :**

1. Exécutez la commande suivante :

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Validation et transmission des modifications :

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Attendez que le déploiement soit terminé.

### Configuration de Google reCAPTCHA ou CAPTCHA

Après avoir installé le package, configurez Google reCAPTCHA (recommandé) ou CAPTCHA comme décrit dans la documentation suivante :

* [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha) dans notre guide d’utilisation.
* [CAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-captcha) dans notre guide d’utilisation.

La nouvelle option de formulaire de passage en caisse est la suivante :

* Google reCAPTCHA : à utiliser dans le formulaire de paiement PayPal Payflow Pro
* CAPTCHA : Payflow Pro

## Assistance et contacts de PayPal

Veuillez contacter le support marchand PayPal pour en savoir plus sur les Services de protection contre les fraudes. Vous pouvez demander à l’équipe de support PayPal d’activer les filtres [Services de protection de base contre les fraudes](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) afin d’offrir un contrôle plus strict possible sur les paiements, de sorte que vous puissiez automatiquement refuser les paiements qui sont susceptibles de générer des transactions frauduleuses et accepter les paiements qui ne posent généralement pas problème. Veuillez noter qu&#39;une fois que vous avez activé les filtres des services de protection contre les fraudes de PayPal, le règlement des transactions peut prendre jusqu&#39;à 2 heures.

>[!NOTE]
>
>Pour plus d’informations, reportez-vous à la section Base de connaissances [ de PayPal qui m’a contacté au sujet de mon intégration à Payflow Pro. Que dois-je faire ?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**Détails de l’assistance du marchand PayPal**

Les heures d’ouverture de la prise en charge de la vente des paiements sont du lundi au vendredi de 7 h 00 à 20 h 00 (heure de la côte ouest). Vous pouvez contacter l’assistance de l’entreprise de paiement pour obtenir de l’aide sur le compte par téléphone ou par courrier électronique :

* Téléphone : 1-888-883-9770 (invite de sélection 2)
* Clients internationaux : 1-408-967-0191
* Adresse électronique : [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Soutien australien

* Lundi au vendredi 8 h - 19 h (heure de l&#39;Union Africaine)
* Téléphone : +61 2 8288 0198
* Adresse électronique : [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
