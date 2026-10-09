---
title: Page du terminal virtuel Braintree Adobe Commerce 2.4.0 corrompue
description: Cet article fournit un correctif pour le problème Adobe Commerce 2.4.0 connu, où la page du terminal virtuel Braintree ne charge pas les éléments d’interface utilisateur appropriés ou un message d’erreur approprié si Braintree n’est pas configuré.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%
---
# Page du terminal virtuel Braintree Adobe Commerce 2.4.0 corrompue

Cet article fournit un correctif pour le problème Adobe Commerce 2.4.0 connu, où la page du terminal virtuel Braintree ne charge pas les éléments d’interface utilisateur appropriés ou un message d’erreur approprié si Braintree n’est pas configuré.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sur l’infrastructure cloud 2.4.0

## Problème

### Scénario 1 : mode de paiement Braintree configuré

<u>Procédure à suivre :</u>

Dans Commerce Admin, accédez à **Ventes** > **Terminal virtuel Braintree** . **&#x200B; **

<u>Résultat attendu : </u>

La page **Braintree Virtual Terminal** se charge avec l’interface utilisateur appropriée.

<u>Résultat réel :</u>

L&#39;interface utilisateur de la page du terminal virtuel **&#x200B;**&#x200B;est endommagée.

### Scénario 2 : mode de paiement Braintree configuré

<u>Procédure à suivre :</u>

Dans Commerce Admin, accédez à **Ventes** > **Terminal virtuel Braintree** . **&#x200B; **

<u>Résultat attendu : </u>

La page **Braintree Virtual Terminal** s’affiche dans l’interface utilisateur appropriée et un avertissement s’affiche pour vous informer que Braintree n’est pas encore configuré.

<u>Résultat réel :</u>

L&#39;interface utilisateur de la page du terminal virtuel **&#x200B;**&#x200B;est endommagée et aucun avertissement ne s&#39;affiche.

## Solution

Appliquez le correctif fourni dans cet article.

## Patch

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Versions d’Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Application du correctif

Pour obtenir des instructions, consultez [Application d’un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) .

## Fichiers attachés
