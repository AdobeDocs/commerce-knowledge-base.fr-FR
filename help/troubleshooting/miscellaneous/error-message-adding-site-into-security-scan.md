---
title: Message d’erreur lors de l’ajout de sites à l’analyse de sécurité
description: Cet article fournit des solutions possibles au problème lorsqu’un utilisateur ne parvient pas à ajouter des sites dans le [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Message d’erreur lors de l’ajout de sites à l’analyse de sécurité

Cet article fournit des solutions possibles au problème lorsqu’un utilisateur n’est pas en mesure d’ajouter des sites dans l’ [analyse de sécurité Commerce](https://account.magento.com/scanner/dashboard/).

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes et versions de déploiement)
* Magento Open Source

## Problème

L’utilisateur n’est pas en mesure d’ajouter des sites dans l’ [analyse de sécurité Commerce](https://account.magento.com/scanner/dashboard/). Le message d’erreur suivant s’affiche lors de la tentative d’ajout d’un site : *Impossible d’envoyer le site pour l’analyse.*

## Solution

1. Assurez-vous que les adresses IP suivantes ne sont pas bloquées sur les ports 80 et 443 :
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. Le code de confirmation est sensible au temps. Si plus de 30 minutes se sont écoulées depuis le clic sur le lien **Ajouter un site**, le code a probablement expiré.
1. N’oubliez pas de nettoyer le cache et de vous assurer que le code de validation apparaît dans le corps de la source de la page d’accueil. Le code de confirmation doit être injecté en fonction des spécifications de balisage de l’HTML : le commentaire de l’HTML peut être injecté dans le corps de la page (nous vous suggérons de le placer dans la section de pied de page) ; la balise META doit se trouver uniquement dans la section head .
1. Avant de cliquer sur **Vérifier le code de confirmation**, ouvrez la console de développement du navigateur, cliquez sur l’onglet **Réseau** et vérifiez la réponse à partir de magento.com. Il doit s’agir de HTTP 200 (OK) et le corps de la réponse doit contenir un objet JSON.
1. Si le code de réponse est HTTP 200 et que le corps de la réponse est un objet JSON et que la valeur de la propriété `verified` est `false`, cela signifie que le code est introuvable sur la page. La valeur de la propriété `details` doit contenir l’explication. Par exemple, si la boutique utilise un certificat SSL auto-signé, il y aura probablement une erreur de connexion.

Si vous ne pouvez toujours pas ajouter de sites, procédez comme suit :

1. Placez un autre commentaire d’HTML sur la page :

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Envoyez un ticket d’assistance et fournissez les informations suivantes :
   * URL du magasin Adobe Commerce
   * MAGEID + Magento.com adresse électronique du compte
   * Prénom + Nom
   * Nom de la société
   * Liste d&#39;emails de notifications séparées par des virgules

## Lecture connexe

* [Analyse de sécurité](https://docs.magento.com/user-guide/magento/security-scan.html) dans notre guide d’utilisation.
