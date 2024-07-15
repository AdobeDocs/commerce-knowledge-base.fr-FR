---
title: Erreur Adobe Commerce 2.4.6 lors du placement de l’ordre à partir du panneau d’administration
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.4.6 lorsque vous êtes bloqué lors de la sélection d’un magasin après avoir passé une commande à partir du panneau d’administration de Commerce.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Erreur Adobe Commerce 2.4.6 lors du placement de l’ordre à partir du panneau d’administration

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.4.6 lorsque vous êtes bloqué lors de la sélection d’un magasin après avoir passé une commande à partir du panneau d’administration de Commerce.

## Problème

Lorsque vous placez une commande à partir du panneau d’administration, vous êtes bloqué lors de la sélection d’un magasin.

<u>Étapes à reproduire</u>

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** et sélectionnez un client pour créer une commande.
2. Sélectionnez le magasin pour passer la commande à partir de l’écran du sélecteur de magasin.

<u>Résultat attendu</u>

Après avoir sélectionné le magasin, vous pouvez terminer la commande.

<u>Résultat réel :</u>

Après avoir sélectionné le magasin, vous êtes redirigé vers la page du sélecteur de magasin et vous ne pouvez pas créer de commande.

## Correctif

Cliquez sur le lien suivant pour télécharger le correctif.

[Téléchargez ACSD-52277_2.4.6.patch.](assets/ACSD-52277_2.4.6.patch.zip)

### Versions Adobe Commerce compatibles

Le correctif a été créé pour et compatible avec Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.4.6 et 2.4.6-p1.

## Comment appliquer le correctif

* Pour plus d’informations sur l’application de correctifs pour Adobe Commerce sur l’infrastructure cloud, reportez-vous à la section [Application de correctifs](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) du guide d’infrastructure de Commerce on Cloud.
* Pour plus d’informations sur l’application de correctifs pour Adobe Commerce sur site, reportez-vous à la section [Application de correctifs](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) du Guide de mise à niveau de Commerce.
