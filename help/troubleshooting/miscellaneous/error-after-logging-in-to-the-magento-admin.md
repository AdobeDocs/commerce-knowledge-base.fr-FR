---
title: Erreur après connexion à l’administrateur Commerce
description: Cet article fournit une solution au problème où vous recevez un message d’erreur indiquant que l’URL demandée est introuvable sur ce serveur.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Erreur après connexion à l’administrateur Commerce

Cet article fournit une solution au problème où vous recevez un message d’erreur indiquant que l’URL demandée est introuvable sur ce serveur.

## Détails

L’URL demandée /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ est introuvable sur ce serveur.

Notez l’absence de barre oblique entre `magento2` et `index.php` dans l’URL.

## Solution

L’URL de base n’est pas correcte. L’URL de base doit :

* Commencer par `http://` ou `https://`
* Terminer par une barre oblique ( `/` )
* Correspondance avec la casse de l’enregistrement `web/unsecure/base_url` dans la table de base de données `core_config_data`

Exécutez à nouveau l’installation à l’aide d’une valeur valide.

## Lecture connexe

[ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
