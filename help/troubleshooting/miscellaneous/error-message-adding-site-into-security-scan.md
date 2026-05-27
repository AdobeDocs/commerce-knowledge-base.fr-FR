---
title: Message d’erreur affiché lors de l’ajout de sites à l’Analyse de sécurité
description: Cet article fournit des solutions possibles au problème lorsqu’un utilisateur ne peut pas ajouter de sites dans l’[Analyse de sécurité Commerce](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Message d’erreur affiché lors de l’ajout de sites à l’Analyse de sécurité

Cet article fournit des solutions possibles au problème lorsqu&#39;un utilisateur ne peut pas ajouter de sites à l&#39;analyse de sécurité Commerce [&#128279;](https://account.magento.com/scanner/dashboard/).

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes et versions de déploiement)
* Magento Open Source

## Problème

L&#39;utilisateur ne peut pas ajouter de sites à l&#39;analyse de sécurité Commerce [&#128279;](https://account.magento.com/scanner/dashboard/). Le message d’erreur suivant s’affiche lors de la tentative d’ajout d’un site : *Impossible d’envoyer le site pour analyse.*

## Solution

1. Assurez-vous que les adresses IP suivantes ne sont pas bloquées sur les ports 80 et 443 :
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. Le code de confirmation est sensible à l’heure. Si plus de 30 minutes se sont écoulées après que l’utilisateur a cliqué sur le lien **Ajouter un site**, le code a probablement expiré.
1. N’oubliez pas de nettoyer le cache et de vous assurer que le code de validation apparaît dans le corps source de la page d’accueil. Le code de confirmation doit être injecté selon les spécifications de balisage d&#39;HTML : le commentaire HTML peut être injecté dans le corps de la page (nous vous suggérons de le placer dans la section de pied de page) ; la balise META ne doit se trouver que dans la section d&#39;en-tête.
1. Avant de cliquer sur **Vérifier le code de confirmation**, ouvrez la console de développement du navigateur, cliquez sur l’onglet **Réseau** et vérifiez la réponse de magento.com. Il doit s’agir de HTTP 200 (OK) et le corps de la réponse doit contenir un objet JSON.
1. Si le code de réponse est HTTP 200 et que le corps de la réponse est un objet JSON et que la valeur de la propriété `verified` est `false`, cela signifie que le code est introuvable sur la page. La valeur de propriété `details` doit contenir l’explication. Par exemple, si le magasin utilise un certificat SSL autosigné, une erreur de connexion se produira probablement.

Si vous ne pouvez toujours pas ajouter de sites, procédez comme suit :

1. Placez un autre commentaire HTML sur la page :

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Envoyez un ticket d’assistance et renseignez les informations suivantes :
   * URL de la boutique Adobe Commerce
   * MAGEID + e-mail du compte Magento.com
   * Prénom + Nom
   * Nom de la société
   * Liste des emails de notification séparés par des virgules

## Lecture connexe

* [Security Scan](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) dans notre guide de l’utilisateur.
