---
title: Échec de l’installation de '[!DNL B2B] 1.4.0 sur Adobe Commerce 2.4.6-p1 sur site'
description: Cet article fournit une solution de contournement pour le problème local d’Adobe Commerce 2.4.6-p1 où l’installation de la version 1.4.0 échoue. [!DNL B2B]
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Échec de l’installation de [!DNL B2B] 1.4.0 sur Adobe Commerce 2.4.6-p1 sur site

Cet article fournit une solution de contournement pour le problème local d’Adobe Commerce 2.4.6-p1 où l’installation de [!DNL B2B] version 1.4.0 échoue.

## Produits et versions concernés

* Adobe Commerce 2.4.6-p1 **sur site**
* [!DNL B2B] version 1.4.0

>[!NOTE]
>
>[!DNL B2B] version 1.4.0 s’installe correctement sur **Adobe Commerce Cloud 2.4.6-p1**.

## Problème

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Essayez d&#39;installer [!DNL B2B] version 1.4.0.

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>Résultats attendus</u> :

[!DNL B2B] version 1.4.0 s’installe correctement sur Adobe Commerce 2.4.6-p1.

<u>Résultats réels</u> :

L&#39;installation échoue avec l&#39;erreur suivante :

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Solution

Installation ou mise à niveau vers la version 1.4.0 de [!DNL B2B] sur Adobe Commerce 2.4.6-p1 avec succès en ajoutant des dépendances manuelles pour le package de sécurité [!DNL B2B] avec une [balise de stabilité](https://getcomposer.org/doc/04-schema.md#package-links).

1. Dans le répertoire d&#39;installation d&#39;Adobe Commerce, mettez à jour `composer.json` avec les dépendances requises :

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Sortie de commande :**

   ```terminal
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Mettez à jour `composer.json` pour ajouter [!DNL B2B] version 1.4.0.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **Sortie de commande :**

   ```terminal
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Procédez à l&#39;installation ou à la mise à niveau.

   * [Installer [!DNL B2B]  sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [Installation sur site](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
