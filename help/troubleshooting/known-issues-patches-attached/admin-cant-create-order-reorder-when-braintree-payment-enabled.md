---
title: L’administrateur ne peut pas créer de commande/réorganisation lorsque le paiement du Braintree est activé
description: Cet article fournit un correctif pour le problème Adobe Commerce 2.4.5, où un utilisateur administrateur ne peut pas créer de commandes ni de commandes pour les clients lorsque le mode de paiement du Braintree est activé.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# L’administrateur ne peut pas créer de commande/réorganisation lorsque le paiement du Braintree est activé

Cet article fournit un correctif pour le problème Adobe Commerce 2.4.5, où un utilisateur administrateur ne peut pas créer de commandes ni de commandes pour les clients lorsque le mode de paiement du Braintree est activé.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.5
* Adobe Commerce sur site 2.4.5
* Magento Open Source 2.4.5

## Problème

<u>Étapes à reproduire</u> :

1. L’intégration de Braintree principal est utilisée (**Magasins** > **Configurations** > **Ventes** > **Méthode de paiement** > **Braintree**).
1. À l’aide de Luma Storefront, passez une commande.
1. Accédez à Admin UI > **Sales**.
1. Essayez de créer une commande pour un client ou accédez à une commande précédemment passée et cliquez sur **Réorganiser**.

<u>Résultat attendu</u> :

Les utilisateurs administrateurs peuvent créer des commandes et des commandes pour les clients avec succès lorsque le mode de paiement du Braintree est activé.

<u>Résultat réel</u> :

Les utilisateurs administrateurs ne peuvent pas créer de commandes ni de commandes pour les clients lorsque le mode de paiement du Braintree est activé, et renvoie l’erreur suivante :

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Cause

Dépendances de classe incorrectes (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, cliquez sur le lien suivant :

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>En outre pour Adobe Commerce sur les marchands d’infrastructure cloud : Adobe a inclus le correctif dans les correctifs cloud pour Commerce version 1.0.18. Reportez-vous aux [notes de mise à jour de Cloud Patches for Commerce](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches) dans notre documentation destinée aux développeurs pour obtenir des instructions sur l’application du dernier package.

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.4.5
* Adobe Commerce sur site 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>Le correctif n’est pas compatible avec les autres versions et éditions Adobe Commerce et Magento Open Source.

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.
