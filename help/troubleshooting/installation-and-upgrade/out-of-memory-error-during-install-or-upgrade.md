---
title: Erreur de mémoire insuffisante lors de l’installation ou de la mise à niveau
description: Cet article traite des solutions pour les erreurs de mémoire insuffisante lors de l’installation/de la mise à niveau des produits Adobe Commerce sur site et Magento Open Source sur site.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Nous vous recommandons [d’allouer 2 Go de mémoire à PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) dans notre documentation destinée aux développeurs pour vous assurer que votre installation ou mise à niveau réussit.

Si vous avez déjà effectué cette opération, créez un fichier de permutation sur votre ordinateur. Une machine Linux utilise *swap space* si elle a besoin de plus de ressources mémoire et si la RAM est pleine. L’espace de permutation est utilisé pour les pages inactives en mémoire.

Vous trouverez ci-dessous des suggestions uniquement ; d’autres options peuvent être disponibles. Consultez un administrateur réseau ou une autre ressource érudite avant de poursuivre. Vous devez exécuter les commandes pour créer un fichier de permutation en tant qu’utilisateur disposant des privilèges `root`.

### Permuter le fichier sur Ubuntu {#swap-file-on-ubuntu}

Utilisez la commande `fallocate` comme décrit dans ces références :

* [Comment ajouter un permutation sur Ubuntu 14.04 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Comment ajouter un espace de permutation sur Ubuntu 16.04 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Permutation de fichier sur CentOS {#swap-file-on-centos}

Utilisez la commande `mkswap` comme décrit dans ces références :

* [Comment ajouter une permutation sur CentOS 6 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Comment ajouter une permutation sur CentOS 7 (Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Swap Space (RedHat customer portal)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
