---
title: Adresse de livraison non enregistrée après actualisation de la page lors du passage en caisse
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.3, où le formulaire d’adresse de livraison déjà renseigné du client était à nouveau vide après avoir actualisé la page du navigateur lors du passage en caisse de l’invité. Le problème survenait lorsque le panier persistant était activé.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Adresse de livraison non enregistrée après actualisation de la page lors du passage en caisse

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.3, où le formulaire d’adresse de livraison déjà renseigné du client était à nouveau vide après avoir actualisé la page du navigateur lors du passage en caisse de l’invité. Le problème survenait lorsque le panier persistant était activé.

## Problème

Les clients passent en caisse et remplissent tous les formulaires, y compris l’adresse de livraison. Ils accèdent à la section Révision et paiements et rechargent la page. Le formulaire est vide et il doit saisir à nouveau l’adresse de livraison. La fonctionnalité de panier persistant est activée.

<u>Étapes à reproduire</u> :

**Conditions préalables**: la fonctionnalité de panier persistant est activée. Vérifiez s’il est activé dans l’Admin, sous **Magasins** > **Configuration** > **Clients** ou **Magasins** > **Configuration** > **Ventes,** selon votre version d’Adobe Commerce.

1. Allez à la vitrine.
1. Ajoutez des produits au panier.
1. Passez à la caisse en tant qu’invité.
1. Renseignez votre adresse d’expédition, sélectionnez les options d’expédition et continuez à sécuriser le paiement.
1. Redirigez-vous vers la section Révision et paiements de l’extraction.
1. Vérifiez que l’adresse de livraison s’affiche dans la section Ship to (Expéditeur).
1. Actualisez la page.

<u>Résultat attendu</u>:

Vous pouvez continuer l’extraction et toutes les données sont enregistrées.

<u>Résultat réel</u>:

L&#39;adresse d&#39;expédition est vide, vous devez la saisir à nouveau.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch.](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Versions Adobe Commerce compatibles

**Le correctif a été créé pour :**

* Adobe Commerce 2.2.3

**Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :**

* Adobe Commerce sur l’infrastructure cloud 2.1.13 - 2.1.18
* Adobe Commerce sur l’infrastructure cloud 2.2.0 - 2.2.5
* Adobe Commerce On-Premise 2.0.X
* Adobe Commerce On-Premise 2.1.X
* Adobe Commerce on-premise 2.2.0 à 2.2.2 et 2.2.4 à 2.2.5

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Fichiers attachés
