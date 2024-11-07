---
title: Problèmes liés aux modules externes du compositeur lors de la mise à niveau vers Adobe Commerce 2.4.4
description: Cet article fournit une solution pour éviter le problème lié aux modules externes de compositeur lors de la mise à niveau d’Adobe Commerce 2.4.3 et versions antérieures vers Adobe Commerce 2.4.4 ou versions ultérieures (lorsque des versions ultérieures sont publiées).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Problèmes liés aux modules externes du compositeur lors de la mise à niveau vers Adobe Commerce 2.4.4

Cet article fournit une solution pour éviter les problèmes liés aux modules externes de compositeur lors de la mise à niveau d’Adobe Commerce 2.4.3 et versions antérieures vers Adobe Commerce 2.4.4 ou versions ultérieures (lorsque de futures versions sont publiées).

## Produits et versions concernés

* Adobe Commerce sur site, toute version lors de la mise à jour vers la version 2.4.4 ou ultérieure (lorsqu’elle est publiée)
* Adobe Commerce sur l’infrastructure cloud, toute version lors de la mise à jour vers la version 2.4.4 ou ultérieure (lorsqu’elle est publiée)
* Magento Open Source, toute version lors de la mise à jour vers la version 2.4.4 ou ultérieure (lorsqu’elle est publiée)

## Problème

Lors d’une mise à jour vers Adobe Commerce 2.4.4 ou version ultérieure après juillet 2022, vous pouvez recevoir un avertissement du compositeur concernant les modules externes.

<u>Étapes à reproduire</u> :

Conditions préalables : Adobe Commerce 2.4.3 ou version antérieure est installé.

1. Démarrez la mise à niveau comme décrit dans [Effectuez une mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Exécutez la commande `composer update` pour mettre à niveau l’application Adobe Commerce.

<u>Résultats attendus</u> :

La mise à niveau a réussi.

<u>Résultats réels</u> :

L&#39;installation échoue avec une erreur similaire à celle-ci :

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Cause

Après juillet 2022, le compositeur modifie la valeur par défaut de l’option [`allow-plugins` ](https://getcomposer.org/doc/06-config.md#allow-plugins) en `{}` et les modules externes ne se chargent plus, sauf si autorisé.

## Solution

Ajoutez ce qui suit à votre fichier `composer.json`, en fonction de la manière dont vous avez installé Adobe Commerce :

* Si le projet a été créé [à l&#39;aide de la commande `composer create-project`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer#get-the-metapackage) :

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Si le projet a été créé d’une autre manière et qu’il ne contient pas `"dealerdirect/phpcodesniffer-installer"` dans la section `"require-dev"` :

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Après la mise à jour du fichier `composer.json`, exécutez la commande `composer update` et redémarrez le processus de mise à niveau.
