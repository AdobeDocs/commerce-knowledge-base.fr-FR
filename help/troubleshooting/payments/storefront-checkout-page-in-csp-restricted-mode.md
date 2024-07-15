---
title: Dépannage de la page de passage en caisse du storefront en mode restreint [!UICONTROL CSP]
description: Cet article explique les erreurs que vous pouvez rencontrer lors de l’affichage de la page de passage en caisse en mode restreint CSP et fournit des solutions pour corriger ces erreurs.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Dépannage de la page de passage en caisse du storefront en mode restreint [!UICONTROL CSP]

Cet article fournit des explications et des correctifs pour les problèmes d’Adobe Commerce 2.4.7 lors de l’affichage de la page de passage en caisse dans **[!UICONTROL CSP restricted mode]**, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, Adobe Commerce sur site et Magento Open Source :

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problème : la page de paiement du storefront est rompue ou ne peut pas se charger

La page **storefront checkout** est rompue ou ne peut pas se charger, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de politique de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u> :

1. Allez à la vitrine.
1. Ajoutez un produit au panier et passez au passage en caisse.

<u>Résultats attendus</u> :

La page de passage en caisse se charge entièrement normalement.

<u>Résultats réels</u> :

La page de passage en caisse est vide ou comporte des composants manquants. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source version 2.4.7 et ultérieure, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Pour résoudre ce problème, vous devez :</u> :

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués utilisant la classe `SecureHtmlRenderer`.
1. Utilisez la classe `CSPNonceProvider` pour permettre l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent un fournisseur **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] pour faciliter la génération de chaînes [!DNL nonce] uniques pour chaque requête. Ces chaînes [!DNL nonce] sont ensuite jointes à l’en-tête [!UICONTROL CSP].

   Utilisez la fonction `generateNonce` de `Magento\Csp\Helper\CspNonceProvider` pour obtenir une chaîne [!DNL nonce].

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

1. [Ajoutez un  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.

## Problème : le mode de paiement est manquant ou ne fonctionne pas

Le mode de paiement est manquant ou ne fonctionne pas sur la page **storefront checkout**, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de politique de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u> :

1. Allez à la vitrine.
2. Ajoutez un produit au panier et passez au passage en caisse.
3. Sélectionnez un mode de paiement.

<u>Résultats attendus</u> :

Vous pouvez sélectionner un mode de paiement et passer une commande avec succès.

<u>Résultats réels</u> :

Le mode de paiement est manquant ou ne fonctionne pas. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source version 2.4.7 et ultérieure, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Pour résoudre ce problème, vous devez :</u> :

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués utilisant la classe `SecureHtmlRenderer`.
1. Utilisez la classe `CSPNonceProvider` pour permettre l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent un fournisseur **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] pour faciliter la génération de chaînes [!DNL nonce] uniques pour chaque requête. Ces chaînes [!DNL nonce] sont ensuite jointes à l’en-tête [!UICONTROL CSP].

   Utilisez la fonction `generateNonce` de `Magento\Csp\Helper\CspNonceProvider` pour obtenir une chaîne [!DNL nonce].

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

1. [Ajoutez un  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.

## Problème : le client ne peut pas passer de commande

Un client ne peut pas passer de commande, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u> :

1. Allez à la vitrine.
2. Ajoutez un produit au panier et passez au passage en caisse.
3. Sélectionnez un mode de paiement.
4. Cliquez sur **Passer commande**.

<u>Résultats attendus</u> :

Vous pouvez passer une commande avec succès.

<u>Résultats réels</u> :

Vous ne pouvez pas passer commande. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source version 2.4.7 et ultérieure, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Pour résoudre ce problème, vous devez :</u> :

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués utilisant la classe `SecureHtmlRenderer`.
1. Utilisez la classe `CSPNonceProvider` pour permettre l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent un fournisseur **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] pour faciliter la génération de chaînes [!DNL nonce] uniques pour chaque requête. Ces chaînes [!DNL nonce] sont ensuite jointes à l’en-tête [!UICONTROL CSP].

   Utilisez la fonction `generateNonce` de `Magento\Csp\Helper\CspNonceProvider` pour obtenir une chaîne [!DNL nonce].

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

1. [Ajoutez un  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.
