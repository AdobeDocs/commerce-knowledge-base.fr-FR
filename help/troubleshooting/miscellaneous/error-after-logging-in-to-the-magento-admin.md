---
title: Erreur après la connexion à l’administrateur Commerce
description: Cet article fournit une solution au problème de réception d’un message d’erreur indiquant que l’URL demandée est introuvable sur ce serveur.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%
---
# Erreur après la connexion à l’administrateur Commerce

Cet article fournit une solution au problème de réception d’un message d’erreur indiquant que l’URL demandée est introuvable sur ce serveur.

## Détails

L’URL demandée /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ est introuvable sur ce serveur.

Notez l’absence de barre oblique entre `magento2` et `index.php` dans l’URL.

## Solution

L’URL de base n’est pas correcte. L’URL de base doit :

* Commencer par `http://` ou `https://`
* Se termine par une barre oblique ( `/` )
* Respecter la casse de l’enregistrement `web/unsecure/base_url` dans la table de base de données `core_config_data`

Réexécutez l’installation à l’aide d’une valeur valide.

## Lecture connexe

[Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
