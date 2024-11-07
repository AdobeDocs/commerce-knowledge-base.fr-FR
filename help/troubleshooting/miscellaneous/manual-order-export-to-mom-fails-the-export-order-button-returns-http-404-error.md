---
title: L’exportation manuelle de la commande vers MOM échoue. Le bouton Export Order renvoie une erreur HTTP 404.
description: Cet article explique comment résoudre un problème en raison duquel la tentative d’exportation d’une commande vers Magento Order Management (MOM) en cliquant sur le bouton **Exporter la commande** dans la vue de commande de l’administrateur Commerce renvoie une erreur "404 Page introuvable*".
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# L’exportation manuelle de la commande vers MOM échoue. Le bouton Export Order renvoie une erreur HTTP 404.

Cet article explique comment résoudre un problème en raison duquel une tentative d’exportation d’une commande vers Magento Order Management (MOM) en cliquant sur le bouton **Exporter la commande** dans la vue de commande de l’administrateur Commerce renvoie une erreur &quot;*404 Page introuvable*&quot;.

## Produits et versions concernés

* Adobe Commerce 2.2.x, 2.3.x
* Connecteur MOM 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problème

<u>Étapes à reproduire :</u> :

1. Dans l’administrateur Commerce, cliquez sur **Ventes > Commandes**.
1. Cliquez sur le bouton **Créer une commande** .
1. Sélectionnez un utilisateur, ajoutez un ou plusieurs éléments, sélectionnez les modes de paiement et d’expédition, puis cliquez sur le bouton **Envoyer la commande** .
1. Cliquez sur le bouton **Export Order** , puis sur **OK**.

<u>Résultat attendu</u> :

La commande est envoyée à MOM.

<u>Résultat réel</u> :

Une page &quot; *404 Error: Page Not Found*&quot; s’affiche.

## Solution

* Mettez à niveau MOM Connector vers la version 3.4.0 pour Adobe Commerce 2.3.x ou MOM Connector 2.5 pour Adobe Commerce 2.2.x.
* Si la mise à niveau de MOM Connector n’est pas une option, vous pouvez exporter l’ordre vers Magento Order Management à l’aide de la commande d’interface de ligne de commande :

```bash
$bin/magento oms:orders:sync
```

## Lecture connexe

[Documentation technique Magento Order Management](https://commerce-docs.github.io/oms-documentation-archive/)
