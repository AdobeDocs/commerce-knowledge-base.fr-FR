---
title: Résolution des problèmes de création de page de commande en mode [!UICONTROL CSP] restreint
description: Cet article explique les erreurs de création d’une commande côté administrateur lorsque le mode restreint de la CSP est activé et fournit des solutions pour corriger ces erreurs.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---

# Résolution des problèmes de création de page de commande en mode [!UICONTROL CSP] restreint

Cet article fournit des explications et des correctifs pour les problèmes d’Adobe Commerce 2.4.7 lors de la création d’une commande côté administrateur avec **[!UICONTROL CSP restricted mode]** est *Activé*, avec le « *Refusé d’exécuter le script intégré, car il enfreint la directive de politique de sécurité du contenu suivante : « script-src ...* » message d’erreur dans le journal de la console du navigateur.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, Adobe Commerce sur site et Magento Open Source :

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problème - La page Admin **créer une commande** est endommagée ou ne peut pas se charger

La page Admin **create order** est endommagée ou ne peut pas être chargée, avec le « *Refusé d’exécuter le script intégré car il viole la directive de la politique de sécurité du contenu suivante : « script-src ...* » message d’erreur dans le journal de la console du navigateur.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Créez une commande.

<u>Résultats attendus</u> :

La page Admin **créer une commande** se charge entièrement normalement.

<u>Résultats réels</u> :

La page Admin **créer une commande** contient des composants vides ou manquants. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : « *Refusé d’exécuter le script intégré, car il viole la directive de politique de sécurité du contenu suivante : « script-src ...* »

### Cause

Dans Adobe Commerce et Magento Open Source versions 2.4.7 et ultérieures, **[!UICONTROL CSP]** est configuré en `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent voir des erreurs de navigateur en raison du blocage de certains scripts en raison de [!UICONTROL CSP] :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Pour résoudre ce problème, vous devez effectuer l’une des opérations suivantes </u> :

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués à l’aide de la classe `SecureHtmlRenderer` .
1. Utilisez la classe `CSPNonceProvider` pour autoriser l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent un fournisseur de [!DNL nonce] **[!UICONTROL Content Security Policy (CSP)]** pour faciliter la génération de chaînes de [!DNL nonce] uniques pour chaque requête. Ces chaînes [!DNL nonce] sont ensuite associées à l’en-tête [!UICONTROL CSP].

   Utilisez la fonction `generateNonce` dans `Magento\Csp\Helper\CspNonceProvider` pour obtenir une chaîne [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Ajoutez a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.

## Problème - Le mode de paiement est manquant ou ne fonctionne pas

Le mode de paiement est manquant ou ne fonctionne pas sur la page Admin **création de commande**, avec le « *Refusé d’exécuter le script intégré, car il enfreint la directive de politique de sécurité du contenu suivante : « script-src ...* » message d’erreur dans le journal de la console du navigateur.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Créez une commande.
1. Créez un nouveau client.
1. Saisissez les détails du client.
1. Saisissez les détails de la commande (produits, mode d’expédition).
1. Sélectionnez un mode de paiement.

<u>Résultats attendus</u> :

Vous pouvez sélectionner un mode de paiement et passer une commande avec succès.

<u>Résultats réels</u> :

Le mode de paiement est manquant ou ne fonctionne pas. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : « *Refusé d’exécuter le script intégré, car il viole la directive de politique de sécurité du contenu suivante : « script-src ...* ».

### Cause

Dans Adobe Commerce et Magento Open Source versions 2.4.7 et ultérieures, **[!UICONTROL CSP]** est configuré en `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent voir des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Pour résoudre ce problème, vous devez effectuer l’une des opérations suivantes </u> :

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués à l’aide de la classe `SecureHtmlRenderer` .
1. Utilisez la classe `CSPNonceProvider` pour autoriser l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent un fournisseur de [!DNL nonce] **[!UICONTROL Content Security Policy (CSP)]** pour faciliter la génération de chaînes de [!DNL nonce] uniques pour chaque requête. Ces chaînes [!DNL nonce] sont ensuite associées à l’en-tête [!UICONTROL CSP].

   Utilisez la fonction `generateNonce` dans `Magento\Csp\Helper\CspNonceProvider` pour obtenir une chaîne [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [ajoutez a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.

## Problème - L’administrateur ne peut pas passer de commande

Un administrateur ne peut pas envoyer de commande sur la page Admin **créer une commande**, avec le « *Refusé d’exécuter le script intégré, car il enfreint la directive de la politique de sécurité du contenu suivante : « script-src ...* » message d’erreur dans le journal de la console du navigateur.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Créez une commande.
1. Créez un nouveau client.
1. Saisissez les détails du client.
1. Saisissez les détails de la commande (produits, mode d’expédition).
1. Sélectionnez un mode de paiement.
1. Soumettez la commande.

<u>Résultats attendus</u> :

Vous pouvez envoyer une commande.

<u>Résultats réels</u> :

Vous ne pouvez pas envoyer de commande. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : « *Refusé d’exécuter le script intégré, car il viole la directive de politique de sécurité du contenu suivante : « script-src ...* »

### Cause

Dans Adobe Commerce et Magento Open Source versions 2.4.7 et ultérieures, **[!UICONTROL CSP]** est configuré en `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent voir des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>Pour résoudre ce problème, vous devez effectuer l’une des opérations suivantes </u> :

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués à l’aide de la classe `SecureHtmlRenderer` .
1. Utilisez la classe `CSPNonceProvider` pour autoriser l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent un fournisseur de [!DNL nonce] **[!UICONTROL Content Security Policy (CSP)]** pour faciliter la génération de chaînes de [!DNL nonce] uniques pour chaque requête. Ces chaînes [!DNL nonce] sont ensuite associées à l’en-tête [!UICONTROL CSP].

   Utilisez la fonction `generateNonce` dans `Magento\Csp\Helper\CspNonceProvider` pour obtenir une chaîne [!DNL nonce].

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Ajoutez a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.
