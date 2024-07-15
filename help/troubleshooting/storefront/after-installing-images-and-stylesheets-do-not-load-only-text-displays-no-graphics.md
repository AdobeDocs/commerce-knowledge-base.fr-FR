---
title: Après l’installation, les images et les feuilles de style ne se chargent pas ; seul le texte s’affiche, aucun graphique
description: Cet article décrit les raisons et solutions possibles pour le problème où les feuilles de style et les images ne se chargent pas après l’installation d’Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Après l’installation, les images et les feuilles de style ne se chargent pas ; seul le texte s’affiche, aucun graphique

Cet article décrit les raisons et solutions possibles pour le problème où les feuilles de style et les images ne se chargent pas après l’installation d’Adobe Commerce.

## Produits et versions concernés

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problème

<u>Étapes à reproduire</u>

1. Installez Adobe Commerce.
1. Accédez au storefront ou à l’administrateur.

<u>Résultat attendu</u>

Des styles sont appliqués, aucun élément d’interface utilisateur ne ressemble à des styles manquants.

<u>Résultat réel</u>

Les styles ne sont pas correctement appliqués, les graphiques sont manquants.

## Cause

Le chemin d’accès aux images et aux feuilles de style n’est pas correct, soit en raison d’une URL de base incorrecte, soit parce que les réécritures du serveur (CentOS, Ubuntu) ne sont pas correctement configurées.

Pour confirmer ce cas, utilisez un inspecteur de navigateur web pour vérifier les chemins d’accès aux ressources statiques et vérifier que ces ressources se trouvent sur le système de fichiers Adobe Commerce ou Magento Open Source.

Les ressources statiques sont situées sous `<magento_root>/pub/static/` , dans les répertoires `frontend` et `adminhtml` .

## Solution

Voici les solutions possibles en fonction du logiciel que vous utilisez et de la cause du problème :

* Si vous utilisez le serveur web Apache, vérifiez le paramètre [server rewrites](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) et l’URL de base de votre serveur Adobe Commerce/Magento Open Source, puis réessayez. Si vous configurez la directive Apache `AllowOverride` de manière incorrecte, les fichiers statiques ne sont pas diffusés à partir du bon emplacement.
* Si vous utilisez le serveur web nginx, veillez à [configurer un fichier d&#39;hôte virtuel](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). Le fichier d’hôte virtuel nginx doit répondre aux critères suivants :
   * La directive `include` doit pointer vers l’exemple de fichier de configuration nginx dans votre répertoire d’installation Adobe Commerce/Magento Open Source. Par exemple :    `include /var/www/html/magento2/nginx.conf.sample;`
   * La directive `server_name` doit correspondre à l’URL de base que vous avez spécifiée lors de l’installation d’Adobe Commerce/Magento Open Source. Par exemple : `server_name 192.186.33.10;`
* Si l’application est en [mode de production](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), essayez de déployer les fichiers d’affichage statique à l’aide de la commande `magento setup:static-content:deploy`. Pour plus d’informations sur le déploiement des fichiers statiques, reportez-vous à la section [Déploiement de fichiers d’affichage statique](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) de notre documentation destinée aux développeurs.
