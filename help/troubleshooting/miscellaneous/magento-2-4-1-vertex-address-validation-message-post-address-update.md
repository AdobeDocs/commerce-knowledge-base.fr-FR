---
title: Adobe Commerce 2.4.1 Message de validation d’adresse de sommet après la mise à jour de l’adresse
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.1 en raison duquel la validation de l’adresse Vertex ne fonctionne pas lors de l’étape de paiement lorsqu’une adresse de livraison différente de l’adresse de facturation est utilisée. Le problème devrait être résolu dans Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Message de validation d’adresse de sommet après la mise à jour de l’adresse

Cet article décrit un problème connu d’Adobe Commerce 2.4.1 en raison duquel la validation de l’adresse Vertex ne fonctionne pas lors de l’étape de paiement lorsqu’une adresse de livraison différente de l’adresse de facturation est utilisée. Le problème devrait être résolu dans Adobe Commerce 2.4.2.

## Produits et versions concernés

* Adobe Commerce On-premise 2.4.1 avec intégration de Vertex activée
* Adobe Commerce sur l’infrastructure cloud 2.4.1 avec l’intégration de Vertex activée

## Problème


<u>Procédure à suivre :</u>

1. Créer un compte et se connecter.
1. Ajoutez un article au panier en cliquant sur **Ajouter au panier**. Cliquez sur l’icône Panier , puis sur **Passer en caisse**.
1. Saisissez une adresse valide dans le champ **Adresse d’expédition**.
1. Cochez l&#39;une des options sous **Modes d&#39;expédition**. Cliquez ensuite sur **Suivant**.
1. Si la validation d’adresse suggère des informations d’adresse différentes, cliquez sur **Mettre à jour l’adresse** puis sur **Suivant**.
1. Décochez la case **Mes adresses de facturation et d’expédition sont les mêmes**.

<u>Premier scénario :</u>

Suivez les [six étapes ci-dessus](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) puis :

1. Saisissez une nouvelle adresse de facturation valide.
1. Cliquez sur le bouton **Mettre à jour**. Le message/la suggestion s’affiche comme suit : *L’adresse n’est pas valide.* Cela s’accompagne d’une suggestion d’adresse telle que : *Code postal : XXXXX- XXXX Rue : XXX Ville rue XXX*
1. Cliquez sur le bouton **Mettre à jour** (ne cliquez pas sur le bouton **Mettre à jour l&#39;adresse** de la suggestion d&#39;adresse de sommet).
1. Cliquez sur le bouton **Modifier** de l’adresse de facturation mise à jour.
1. Sélectionnez l’adresse dans la liste déroulante Adresse .
1. Cliquez sur le bouton **Mettre à jour**.

<u>Résultat attendu : </u>

L’ancien message de validation/suggestion est supprimé.

<u>Résultat réel :</u>

Le message/la suggestion de validation *« Nous n’avons pas trouvé d’adresse valide Code postal : XXXXX-XXXX Rue : XXX Ville rue XXX »* message est **NON** supprimé. Le même problème se produit si vous saisissez une adresse non valide dans le formulaire.

<u>Deuxième scénario :</u>

Suivez les [six étapes ci-dessus](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) puis :

1. Remplissez le formulaire d’adresse avec une adresse valide.
1. Cliquez sur le bouton **Mettre à jour**. Le message/la suggestion s’affiche comme suit : *L’adresse n’est pas valide.* Cela s’accompagne d’une suggestion d’adresse telle que : *Code postal : XXXXX-XXXX Rue : XXX Ville XXX*.
1. Cliquez sur le bouton **Mettre à jour** (ne cliquez pas sur le bouton **Mettre à jour l&#39;adresse** de la suggestion d&#39;adresse de sommet).
1. Vérifiez le menu déroulant ***Mes adresses de facturation et d’expédition sont les mêmes***.

<u>Résultat attendu : </u>

L’ancien message de validation/suggestion est supprimé.

<u>Résultat réel :</u>

Le message/la suggestion de validation *« Nous n’avons pas trouvé d’adresse valide Code postal : XXXXX-XXXX Rue XXX Ville rue XXX »* message est **NON** supprimé. Le même problème se produit si vous saisissez une adresse non valide dans le formulaire.

## Informations connexes dans notre base de connaissances de support :

[Adobe Commerce 2.3.6, 2.4.0-p1 et 2.4.1 problème connu : impossible de se connecter à dotdigital lorsque le compte est activé](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
