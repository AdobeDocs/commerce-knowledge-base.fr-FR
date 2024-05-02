---
title: Erreur 503 lors de l’accès à Adobe Commerce dans le navigateur web
description: Cet article fournit une solution possible au problème d’erreur 503 qui se produit lorsque vous tentez d’accéder au storefront et/ou à l’administrateur d’Adobe Commerce.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Erreur 503 lors de l’accès à Adobe Commerce dans le navigateur web

Cet article fournit une solution possible au problème d’erreur 503 qui se produit lorsque vous tentez d’accéder au storefront et/ou à l’administrateur d’Adobe Commerce.

## Produits et versions concernés

Adobe Commerce 2.3.x

## Problème {#symptoms}

<u>Étapes à reproduire</u>

(Conditions préalables : assurez-vous que le magasin ne se trouve pas dans [mode de maintenance](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-mode.html#config-mode-show)).

Accédez à votre administrateur Commerce ou à votre vitrine dans un navigateur web.

<u>Résultat attendu</u>

La page se charge.

<u>Résultat réel</u>

Vous obtenez l’erreur HTTP 503 (Service non disponible). Apache `error.log` inclut le message suivant :

*Commande non valide &quot;Order&quot;, peut-être mal orthographiée ou définie par un module non inclus dans la configuration du serveur.*

## Cause {#details}

Module de compatibilité Apache 2.4 `mod_access_compat` est désactivée, ce qui entraîne une réécriture de l’URL Adobe Commerce qui ne fonctionne pas correctement.

## Solution {#suggested-solution}

Activez la variable `mod_access_compat` Module Apache et redémarrez Apache, en exécutant ce qui suit en tant qu’utilisateur avec les privilèges &quot;root&quot; :

```bash
a2enmod access_compat
service <name> restart
```

Sous CentOS,

```bash
<name>
```

is

```bash
httpd
```

. Sur Ubuntu,

```bash
<name>
```

is

```bash
apache2
```

.

## Lecture connexe {#additional-resources}

* [Documentation Apache sur mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Documentation Apache sur mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Ordre, autorisation et refus dans le guide de définition Apache](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
