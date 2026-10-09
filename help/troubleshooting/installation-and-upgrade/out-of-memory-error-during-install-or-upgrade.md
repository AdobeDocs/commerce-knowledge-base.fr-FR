---
title: Erreur de mémoire insuffisante lors de l’installation ou de la mise à niveau
description: Cet article présente des solutions pour l’erreur de mémoire insuffisante lors de l’installation/la mise à niveau des produits Adobe Commerce on-premise et Magento Open Source on-premise.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%
---
# Erreur de mémoire insuffisante lors de l’installation ou de la mise à niveau

Cet article présente des solutions pour l’erreur de mémoire insuffisante lors de l’installation/la mise à niveau des produits Adobe Commerce on-premise et Magento Open Source on-premise.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.x
* Magento Open Source on-premise 2.3.x

## Problème

Lors de l’installation ou de la mise à jour de l’application Adobe Commerce ou Magento Open Source ou de composants tels que des extensions, des thèmes ou des packages de langue, à l’aide de l’assistant Configuration Web, une erreur similaire à celle-ci s’affiche :

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

L’erreur

```bash
proc_open(): fork failed - Cannot allocate memory
```

peut également s’afficher sur la ligne de commande.

## Solution {#solution}

Nous vous recommandons [d’allouer 2 Go de mémoire à PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) dans notre documentation destinée aux développeurs afin de garantir le succès de votre installation ou de votre mise à niveau.

Si vous l&#39;avez déjà fait, créez un fichier d&#39;échange sur votre ordinateur. Une machine Linux utilise *swap space* si elle a besoin de plus de ressources mémoire et que la RAM est pleine. L’espace de permutation est utilisé pour les pages inactives en mémoire.

Voici quelques suggestions uniquement ; d’autres options peuvent être disponibles. Consultez un administrateur réseau ou une autre personne compétente avant de continuer. Vous devez exécuter les commandes pour créer un fichier d&#39;échange en tant qu&#39;utilisateur disposant de privilèges `root`.

### Permuter le fichier sur Ubuntu {#swap-file-on-ubuntu}

Utilisez la commande `fallocate` comme indiqué dans les références suivantes :

* [Comment ajouter Swap sur Ubuntu 14.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Comment ajouter de l&#39;espace d&#39;échange sur Ubuntu 16.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Permuter le fichier sous CentOS {#swap-file-on-centos}

Utilisez la commande `mkswap` comme indiqué dans les références suivantes :

* [Comment ajouter Swap sur CentOS 6 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Comment ajouter Swap sur CentOS 7 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Espace d’échange (portail client Red Hat)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
