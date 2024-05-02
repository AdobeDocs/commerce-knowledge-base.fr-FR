---
title: Erreur de mémoire insuffisante lors de l’installation ou de la mise à niveau
description: Cet article traite des solutions pour les erreurs de mémoire insuffisante lors de l’installation/de la mise à niveau des produits Adobe Commerce sur site et Magento Open Source sur site.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Erreur de mémoire insuffisante lors de l’installation ou de la mise à niveau

Cet article traite des solutions pour les erreurs de mémoire insuffisante lors de l’installation/de la mise à niveau des produits Adobe Commerce sur site et Magento Open Source sur site.

## Produits et versions concernés

* Adobe Commerce On-Premise 2.3.x
* Magento Open Source on-premise 2.3.x

## Problème

Lors de l’installation ou de la mise à jour d’une application ou de composants Adobe Commerce ou Magento Open Source tels que des extensions, des thèmes ou des modules de langue, à l’aide de l’assistant de configuration web, une erreur similaire à celle-ci s’affiche :

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

L&#39;erreur

```bash
proc_open(): fork failed - Cannot allocate memory
```

peut également s’afficher sur la ligne de commande.

## Solution {#solution}

Nous vous recommandons [Allouer 2 Go de mémoire à PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) dans notre documentation destinée aux développeurs pour vous assurer que votre installation ou mise à niveau réussit.

Si vous avez déjà effectué cette opération, créez un fichier de permutation sur votre ordinateur. Une machine Linux utilise *espace d’échange* s’il a besoin de davantage de ressources mémoire et que la mémoire vive est pleine. L’espace de permutation est utilisé pour les pages inactives en mémoire.

Vous trouverez ci-dessous des suggestions uniquement ; d’autres options peuvent être disponibles. Consultez un administrateur réseau ou une autre ressource érudite avant de poursuivre. Vous devez exécuter les commandes pour créer un fichier de permutation en tant qu’utilisateur avec `root` des privilèges.

### Permuter le fichier sur Ubuntu {#swap-file-on-ubuntu}

Utilisez la variable `fallocate` comme décrit dans ces références :

* [Comment ajouter l’échange sur Ubuntu 14.04 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Comment ajouter un espace de permutation sur Ubuntu 16.04 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Permutation de fichier sur CentOS {#swap-file-on-centos}

Utilisez la variable `mkswap` comme décrit dans ces références :

* [Comment ajouter une permutation sur CentOS 6 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Comment ajouter une permutation sur CentOS 7 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Swap Space (portail client RedHat)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
