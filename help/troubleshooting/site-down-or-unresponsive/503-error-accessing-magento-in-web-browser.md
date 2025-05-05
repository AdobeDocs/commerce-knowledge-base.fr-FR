---
title: Erreur 503 lors de l’accès à Adobe Commerce dans le navigateur web
description: Cet article fournit une solution possible au problème d’erreur 503 qui se produit lorsque vous tentez d’accéder au storefront et/ou à l’administrateur d’Adobe Commerce.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

(Conditions préalables : assurez-vous que le magasin n’est pas en [mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show)).

Accédez à votre administrateur Commerce ou à votre vitrine dans un navigateur web.

<u>Résultat attendu</u>

La page se charge.

<u>Résultat réel</u>

Vous obtenez l’erreur HTTP 503 (Service non disponible). L&#39;Apache `error.log` comprend le message suivant :

*Commande non valide &#39;Order&#39;, peut-être mal orthographiée ou définie par un module non inclus dans la configuration du serveur.*

## Cause {#details}

Le module de compatibilité Apache 2.4 `mod_access_compat` est désactivé, ce qui entraîne une réécriture de l’URL Adobe Commerce qui ne fonctionne pas correctement.

## Solution {#suggested-solution}

Activez le module Apache `mod_access_compat` et redémarrez Apache en exécutant les opérations suivantes en tant qu’utilisateur avec les privilèges &#39;root&#39; :

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
* [Commande, autorisation, refus du Guide de définition Apache](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
