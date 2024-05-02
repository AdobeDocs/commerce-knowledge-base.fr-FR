---
title: Dépannage de la page de passage en caisse du storefront dans [!UICONTROL CSP] mode restreint
description: Cet article explique les erreurs que vous pouvez rencontrer lors de l’affichage de la page de passage en caisse en mode restreint CSP et fournit des solutions pour corriger ces erreurs.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Dépannage de la page de passage en caisse du storefront dans [!UICONTROL CSP] mode restreint

Cet article fournit des explications et des correctifs pour les problèmes d’Adobe Commerce 2.4.7 lors de l’affichage de la page de passage en caisse dans **[!UICONTROL CSP restricted mode]**, avec le *Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, Adobe Commerce sur site et Magento Open Source :

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problème : la page de paiement du storefront est rompue ou ne peut pas se charger

La variable **paiement storefront** La page est rompue ou ne peut pas se charger, avec le *Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u>:

1. Allez à la vitrine.
1. Ajoutez un produit au panier et passez au passage en caisse.

<u>Résultats attendus</u>:

La page de passage en caisse se charge entièrement normalement.

<u>Résultats réels</u>:

La page de passage en caisse est vide ou comporte des composants manquants. Les éléments suivants [!DNL JS] s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source versions 2.4.7 et ultérieures, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et dans `report-only` pour toutes les autres pages.
La variable **[!UICONTROL CSP]** L’en-tête ne contient pas `unsafe-inline` dans le `script-src` pour les pages de paiement. En outre, uniquement [!DNL whitelisted] les scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts. **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Pour résoudre ce problème, vous devez :</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués à l’aide de la fonction `SecureHtmlRenderer` classe .
1. Utilisez la variable `CSPNonceProvider` pour permettre l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent une **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] fournisseur pour faciliter la génération de [!DNL nonce] pour chaque requête. Ces [!DNL nonce] les chaînes sont ensuite associées à la fonction [!UICONTROL CSP] en-tête .

   Utilisez la variable `generateNonce` fonction dans `Magento\Csp\Helper\CspNonceProvider` pour obtenir un [!DNL nonce] chaîne.

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

1. [Ajouter un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) à la fonction `csp_whitelist.xml` fichier .

## Problème : le mode de paiement est manquant ou ne fonctionne pas

Le mode de paiement est absent ou ne fonctionne pas sur la variable **paiement storefront** , avec le *Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u>:

1. Allez à la vitrine.
2. Ajoutez un produit au panier et passez au passage en caisse.
3. Sélectionnez un mode de paiement.

<u>Résultats attendus</u>:

Vous pouvez sélectionner un mode de paiement et passer une commande avec succès.

<u>Résultats réels</u>:

Le mode de paiement est manquant ou ne fonctionne pas. Les éléments suivants [!DNL JS] s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source versions 2.4.7 et ultérieures, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et dans `report-only` pour toutes les autres pages.
La variable **[!UICONTROL CSP]** L’en-tête ne contient pas `unsafe-inline` dans le `script-src` pour les pages de paiement. En outre, uniquement [!DNL whitelisted] les scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts. **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Pour résoudre ce problème, vous devez :</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués à l’aide de la fonction `SecureHtmlRenderer` classe .
1. Utilisez la variable `CSPNonceProvider` pour permettre l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent une **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] fournisseur pour faciliter la génération de [!DNL nonce] pour chaque requête. Ces [!DNL nonce] les chaînes sont ensuite associées à la fonction [!UICONTROL CSP] en-tête .

   Utilisez la variable `generateNonce` fonction dans `Magento\Csp\Helper\CspNonceProvider` pour obtenir un [!DNL nonce] chaîne.

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

1. [Ajouter un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) à la fonction `csp_whitelist.xml` fichier .

## Problème : le client ne peut pas passer de commande

Un client ne peut pas passer de commande, avec le *Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u>:

1. Allez à la vitrine.
2. Ajoutez un produit au panier et passez au passage en caisse.
3. Sélectionnez un mode de paiement.
4. Cliquez sur **Passer commande**.

<u>Résultats attendus</u>:

Vous pouvez passer une commande avec succès.

<u>Résultats réels</u>:

Vous ne pouvez pas passer commande. Les éléments suivants [!DNL JS] s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source versions 2.4.7 et ultérieures, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et dans `report-only` pour toutes les autres pages.
La variable **[!UICONTROL CSP]** L’en-tête ne contient pas `unsafe-inline` dans le `script-src` pour les pages de paiement. En outre, uniquement [!DNL whitelisted] les scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts. **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Pour résoudre ce problème, vous devez :</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) les scripts bloqués à l’aide de la fonction `SecureHtmlRenderer` classe .
1. Utilisez la variable `CSPNonceProvider` pour permettre l’exécution des scripts.
Adobe Commerce et Magento Open Source 2.4.7 et versions ultérieures incluent une **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] fournisseur pour faciliter la génération de [!DNL nonce] pour chaque requête. Ces [!DNL nonce] les chaînes sont ensuite associées à la fonction [!UICONTROL CSP] en-tête .

   Utilisez la variable `generateNonce` fonction dans `Magento\Csp\Helper\CspNonceProvider` pour obtenir un [!DNL nonce] chaîne.

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

1. [Ajouter un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) à la fonction `csp_whitelist.xml` fichier .
