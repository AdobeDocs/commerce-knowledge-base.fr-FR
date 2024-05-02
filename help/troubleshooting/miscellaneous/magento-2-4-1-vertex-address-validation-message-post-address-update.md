---
title: Mise à jour de l’adresse de message après validation de l’adresse du sommet Adobe Commerce 2.4.1
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel la validation de l’adresse Vertex ne fonctionne pas lors de l’étape de paiement lorsqu’une adresse de livraison est utilisée, et qui diffère de l’adresse de facturation. Le problème doit être corrigé dans Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Mise à jour de l’adresse de message après validation de l’adresse du sommet Adobe Commerce 2.4.1

Cet article décrit un problème connu d’Adobe Commerce 2.4.1, en raison duquel la validation de l’adresse Vertex ne fonctionne pas lors de l’étape de paiement lorsqu’une adresse de livraison est utilisée, et qui diffère de l’adresse de facturation. Le problème doit être corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.1 avec l’intégration de Vertex activée
* Adobe Commerce sur l’infrastructure cloud 2.4.1 avec l’intégration de Vertex activée

## Problème

Conditions préalables :

Activer **Nettoyage des adresses de sommet**. Pour connaître les étapes, voir [Configuration du nettoyage des adresses de Storefront](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) dans notre guide d’utilisation.

<u>Étapes à reproduire :</u>

1. Créez un compte et connectez-vous.
1. Ajoutez un élément au panier en cliquant sur **Ajouter au panier**. Cliquez sur l’icône Panier, puis sur **Passez à l’extraction**.
1. Saisissez une adresse valide dans le champ **Adresse d’expédition** champ .
1. Cochez l’une des options situées sous **Méthodes d’expédition**. Cliquez ensuite sur **Suivant**.
1. Si la validation de l’adresse suggère des informations d’adresse différentes, cliquez sur **Mettre à jour l&#39;adresse** et cliquez sur **Suivant**.
1. Décochez la case **Mes adresses de facturation et de livraison sont les mêmes** .

<u>Premier scénario :</u>

Suivez la [six étapes au-dessus](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) puis :

1. Saisissez une nouvelle adresse de facturation valide.
1. Cliquez sur le bouton **Mettre à jour** bouton . Il affiche le message/la suggestion comme suit : *L’adresse n’est pas valide.* Ensuite, une suggestion d’adresse s’affichera : *Code postal : XXXXX- XXXX Street : XXX City street XXX*
1. Cliquez sur le bouton **Mettre à jour** (ne cliquez pas sur le bouton **Mettre à jour l&#39;adresse** de la suggestion d’adresse de sommet).
1. Cliquez sur le bouton **Modifier** de l&#39;adresse de facturation mise à jour.
1. Sélectionnez l’adresse dans la liste déroulante des adresses.
1. Cliquez sur le bouton **Mettre à jour** bouton .

<u>Résultat attendu :</u>

L’ancien message de validation/suggestion est supprimé.

<u>Résultat réel :</u>

Message/suggestion de validation *&quot;Nous n&#39;avons pas trouvé d&#39;adresse valide Postcode : XXXXX-XXXX Street : XXX City street XXX&quot;* message is **NOT** supprimé. Le même problème se produit si vous saisissez une adresse non valide dans le formulaire.

<u>Deuxième scénario :</u>

Suivez la [six étapes au-dessus](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) puis :

1. Remplissez le formulaire d&#39;adresse avec une adresse valide.
1. Cliquez sur le bouton **Mettre à jour** bouton . Il affiche le message/la suggestion comme suit : *L’adresse n’est pas valide.* Ensuite, une suggestion d’adresse s’affichera : *Code postal : rue XXXXX-XXXX : rue XXX Ville XXX*.
1. Cliquez sur le bouton **Mettre à jour** (ne cliquez pas sur le bouton **Mettre à jour l&#39;adresse** bouton de suggestion d’adresse de sommet).
1. Vérifiez les ***Mes adresses de facturation et de livraison sont les mêmes*** menu déroulant.

<u>Résultat attendu :</u>

L’ancien message de validation/suggestion est supprimé.

<u>Résultat réel :</u>

Message/suggestion de validation *&quot;Nous n&#39;avons pas trouvé d&#39;adresse valide Postcode : XXXXX-XXXX Street XXX City street XXX&quot;* message is **NOT** supprimé. Le même problème se produit si vous saisissez une adresse non valide dans le formulaire.

## Lecture connexe dans notre base de connaissances de soutien :

[Problème connu d’Adobe Commerce 2.3.6, 2.4.0-p1 et 2.4.1 : connexion à dodigital impossible lorsque le compte est activé](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
