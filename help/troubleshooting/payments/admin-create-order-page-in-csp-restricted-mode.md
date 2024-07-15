---
title: Dépannage de la création de page de commande en mode restreint [!UICONTROL CSP]
description: Cet article explique les erreurs lors de la création d’une commande côté administrateur lorsque le mode restreint CSP est activé et fournit des solutions pour corriger ces erreurs.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Dépannage de la création de page de commande en mode restreint [!UICONTROL CSP]

Cet article fournit des explications et des correctifs pour les problèmes d’Adobe Commerce 2.4.7 lors de la création d’une commande côté administrateur avec **[!UICONTROL CSP restricted mode]** est *Activé*, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, Adobe Commerce sur site et Magento Open Source :

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problème : la page **créer l’ordre** de l’administrateur est endommagée ou ne peut pas se charger

La page **créer l’ordre** de l’administrateur est rompue ou ne peut pas se charger, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de stratégie de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Créez une commande.

<u>Résultats attendus</u> :

La page **de création d’ordre** de l’administrateur charge complètement normalement.

<u>Résultats réels</u> :

La page **créer une commande** de l’administrateur est vide ou comporte des composants manquants. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source version 2.4.7 et ultérieure, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts en raison de [!UICONTROL CSP] :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

Le mode de paiement est manquant ou ne fonctionne pas sur la **page de création de commande** de l’administrateur, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de stratégie de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Créez une commande.
1. Créez un client.
1. Saisissez les détails du client.
1. Renseignez les détails de la commande (produits, mode de livraison).
1. Sélectionnez un mode de paiement.

<u>Résultats attendus</u> :

Vous pouvez sélectionner un mode de paiement et passer une commande avec succès.

<u>Résultats réels</u> :

Le mode de paiement est manquant ou ne fonctionne pas. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré car il enfreint la directive suivante de la stratégie de sécurité du contenu : &quot;script-src ...*&quot;.

### Cause

Dans Adobe Commerce et Magento Open Source version 2.4.7 et ultérieure, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

1. [ajoutez une  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) au fichier `csp_whitelist.xml` de votre module.

## Problème : l’administrateur ne peut pas passer de commande

Un administrateur ne peut pas envoyer de commande sur la **page de création d’une commande** de l’administrateur, avec le message d’erreur &quot;*Refusé d’exécuter le script intégré, car il enfreint la directive de stratégie de sécurité du contenu suivante : &quot;script-src ...*&quot; dans le journal de la console du navigateur.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Créez une commande.
1. Créez un client.
1. Saisissez les détails du client.
1. Renseignez les détails de la commande (produits, mode de livraison).
1. Sélectionnez un mode de paiement.
1. Envoyez la commande.

<u>Résultats attendus</u> :

Vous pouvez envoyer une commande avec succès.

<u>Résultats réels</u> :

Vous ne pouvez pas envoyer de commande. L’erreur [!DNL JS] suivante s’affiche dans le journal de la console du navigateur : &quot;*Refusé d’exécuter le script intégré car il enfreint la directive de sécurité du contenu suivante : &quot;script-src ...*&quot;

### Cause

Dans Adobe Commerce et Magento Open Source version 2.4.7 et ultérieure, **[!UICONTROL CSP]** est configuré dans `restrict-mode`, par défaut, pour les pages de paiement dans les zones storefront et admin, et en mode `report-only` pour toutes les autres pages.
L’en-tête **[!UICONTROL CSP]** correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls [!DNL whitelisted] scripts intégrés sont autorisés.

### Solution

Les utilisateurs peuvent rencontrer des erreurs de navigateur en raison du blocage de certains scripts en raison de **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
